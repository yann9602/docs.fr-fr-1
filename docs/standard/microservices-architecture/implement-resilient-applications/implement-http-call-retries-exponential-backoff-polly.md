---
title: "Implémenter des tentatives d’appel HTTP avec interruption exponentielle avec Polly"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémenter des tentatives d’appel HTTP avec interruption exponentielle avec Polly"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1ed48142546403ea710f4c132e038521232c20ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="71a1d-104">Implémenter des tentatives d’appel HTTP avec interruption exponentielle avec Polly</span><span class="sxs-lookup"><span data-stu-id="71a1d-104">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="71a1d-105">L’approche recommandée pour les nouvelles tentatives avec interruption exponentielle consiste à tirer parti des bibliothèques de .NET plus avancées telles qu’open source [Polly](https://github.com/App-vNext/Polly) bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="71a1d-105">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="71a1d-106">Polly est une bibliothèque .NET qui fournit la résilience et fonctionnalités de gestion d’erreurs de temporaire.</span><span class="sxs-lookup"><span data-stu-id="71a1d-106">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="71a1d-107">Vous pouvez implémenter ces fonctionnalités facilement en appliquant des stratégies Polly telles que la nouvelle tentative, disjoncteur, d’Isolation de cloisonnement, délai d’attente et de secours.</span><span class="sxs-lookup"><span data-stu-id="71a1d-107">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="71a1d-108">Polly cible .NET 4.x et Standard .NET version 1.0 (qui prend en charge de .NET Core).</span><span class="sxs-lookup"><span data-stu-id="71a1d-108">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="71a1d-109">La stratégie de nouvelle tentative dans Polly est l’approche utilisée dans eShopOnContainers lors de l’implémentation de tentatives HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a1d-109">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="71a1d-110">Vous pouvez implémenter une interface afin de vous pouvez injecter fonctionnalité HttpClient standard ou une version résiliente de client HTTP à l’aide de Polly, selon quelle configuration de stratégie de nouvelle tentative à utiliser.</span><span class="sxs-lookup"><span data-stu-id="71a1d-110">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="71a1d-111">L’exemple suivant montre l’interface implémentée dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="71a1d-111">The following example shows the interface implemented in eShopOnContainers.</span></span>

```csharp
public interface IHttpClient
{
    Task<string> GetStringAsync(string uri, string authorizationToken = null,
        string authorizationMethod = "Bearer");
        Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    Task<HttpResponseMessage> DeleteAsync(string uri,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    // Other methods ...
}
```

<span data-ttu-id="71a1d-112">Vous pouvez utiliser l’implémentation standard si vous ne souhaitez pas utiliser un mécanisme souple, comme lorsque vous développez ou approches plus simples de tests.</span><span class="sxs-lookup"><span data-stu-id="71a1d-112">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="71a1d-113">Le code suivant affiche les demandes autoriser standards HttpClient mise en œuvre avec les jetons d’authentification comme un cas facultatif.</span><span class="sxs-lookup"><span data-stu-id="71a1d-113">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

```csharp
public class StandardHttpClient : IHttpClient
{
    private HttpClient _client;
    private ILogger<StandardHttpClient> _logger;

    public StandardHttpClient(ILogger<StandardHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
    }

    public async Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
        if (authorizationToken != null)
        {
            requestMessage.Headers.Authorization =
                new AuthenticationHeaderValue(authorizationMethod, authorizationToken);
        }
        var response = await _client.SendAsync(requestMessage);
        return await response.Content.ReadAsStringAsync();
    }

    public async Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer")
    {
        // Rest of the code and other Http methods ...
```

<span data-ttu-id="71a1d-114">L’implémentation intéressante consiste à un autre, de la même classe, mais à l’aide de Polly pour implémenter les mécanismes résilients que vous souhaitez utiliser le code, dans l’exemple suivant, effectue une nouvelle tentative avec interruption exponentielle.</span><span class="sxs-lookup"><span data-stu-id="71a1d-114">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

```csharp
public class ResilientHttpClient : IHttpClient
{
    private HttpClient _client;
    private PolicyWrap _policyWrapper;
    private ILogger<ResilientHttpClient> _logger;

    public ResilientHttpClient(Policy[] policies,
        ILogger<ResilientHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
        // Add Policies to be applied
        _policyWrapper = Policy.WrapAsync(policies);
    }

    private Task<T> HttpInvoker<T>(Func<Task<T>> action)
    {
        // Executes the action applying all
        // the policies defined in the wrapper
        return _policyWrapper.ExecuteAsync(() => action());
    }

    public Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        return HttpInvoker(async () =>
        {
            var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
            // The Token's related code eliminated for clarity in code snippet
            var response = await _client.SendAsync(requestMessage);
            return await response.Content.ReadAsStringAsync();
        });
    }
    // Other Http methods executed through HttpInvoker so it applies Polly policies
    // ...
}
```

<span data-ttu-id="71a1d-115">Avec Polly, vous définissez une stratégie de nouvelle tentative avec le nombre de nouvelles tentatives, la configuration de l’interruption exponentielle et les actions à entreprendre lorsqu’il existe une exception HTTP, telles que la journalisation de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="71a1d-115">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="71a1d-116">Dans ce cas, la stratégie est configurée afin qu’il va tenter du nombre de fois spécifié lors de l’inscription des types dans le conteneur inversion de contrôle.</span><span class="sxs-lookup"><span data-stu-id="71a1d-116">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="71a1d-117">En raison de la configuration de l’interruption exponentielle, chaque fois que le code détecte une exception HttpRequest, il retente la demande Http après un laps de temps qui augmente de façon exponentielle en fonction de la configuration de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="71a1d-117">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="71a1d-118">La méthode importante est HttpInvoker, ce qui rend les requêtes HTTP tout au long de cette classe d’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="71a1d-118">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="71a1d-119">Que méthode interne s’exécute la requête HTTP avec \_policyWrapper.ExecuteAsync, qui prend en compte la stratégie de nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="71a1d-119">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="71a1d-120">Dans eShopOnContainers vous spécifiez des stratégies de Polly lors de l’inscription des types au niveau du conteneur inversion de contrôle, comme dans le code suivant à partir de la [application web MVC est à le startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) classe.</span><span class="sxs-lookup"><span data-stu-id="71a1d-120">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

```csharp
// Startup.cs class
if (Configuration.GetValue<string>("UseResilientHttp") == bool.TrueString)
{
    services.AddTransient<IResilientHttpClientFactory,
        ResilientHttpClientFactory>();
    services.AddSingleton<IHttpClient,
        ResilientHttpClient>(sp =>
            sp.GetService<IResilientHttpClientFactory>().
            CreateResilientHttpClient());
}
else
{
    services.AddSingleton<IHttpClient, StandardHttpClient>();
}
```

<span data-ttu-id="71a1d-121">Notez que les objets IHttpClient sont instanciés en tant que singleton au lieu de comme transitoire afin que les connexions TCP sont utilisées efficacement par le service et [un problème avec les sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) n’a pas lieu.</span><span class="sxs-lookup"><span data-stu-id="71a1d-121">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="71a1d-122">Cependant, le point important sur la résilience est que vous appliquez la stratégie Polly WaitAndRetryAsync dans ResilientHttpClientFactory dans la méthode CreateResilientHttpClient, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="71a1d-122">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

// Other code
private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
        // number of retries
        6,
        // exponential backoff
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
        // on retry
        (exception, timeSpan, retryCount, context) =>
        {
            var msg = $"Retry {retryCount} implemented with Pollys RetryPolicy " +
            $"of {context.PolicyKey} " +
            $"at {context.ExecutionKey}, " +
            $"due to: {exception}.";
            _logger.LogWarning(msg);
            _logger.LogDebug(msg);
        }),
    }
```


>[!div class="step-by-step"]
<span data-ttu-id="71a1d-123">[Précédente] (implement-custom-http-call-retries-exponential-backoff.md) [suivant] (implémentez-circuit-analyseur lexical-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="71a1d-123">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>
