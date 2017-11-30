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
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a>Implémenter des tentatives d’appel HTTP avec interruption exponentielle avec Polly

L’approche recommandée pour les nouvelles tentatives avec interruption exponentielle consiste à tirer parti des bibliothèques de .NET plus avancées telles qu’open source [Polly](https://github.com/App-vNext/Polly) bibliothèque.

Polly est une bibliothèque .NET qui fournit la résilience et fonctionnalités de gestion d’erreurs de temporaire. Vous pouvez implémenter ces fonctionnalités facilement en appliquant des stratégies Polly telles que la nouvelle tentative, disjoncteur, d’Isolation de cloisonnement, délai d’attente et de secours. Polly cible .NET 4.x et Standard .NET version 1.0 (qui prend en charge de .NET Core).

La stratégie de nouvelle tentative dans Polly est l’approche utilisée dans eShopOnContainers lors de l’implémentation de tentatives HTTP. Vous pouvez implémenter une interface afin de vous pouvez injecter fonctionnalité HttpClient standard ou une version résiliente de client HTTP à l’aide de Polly, selon quelle configuration de stratégie de nouvelle tentative à utiliser.

L’exemple suivant montre l’interface implémentée dans eShopOnContainers.

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

Vous pouvez utiliser l’implémentation standard si vous ne souhaitez pas utiliser un mécanisme souple, comme lorsque vous développez ou approches plus simples de tests. Le code suivant affiche les demandes autoriser standards HttpClient mise en œuvre avec les jetons d’authentification comme un cas facultatif.

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

L’implémentation intéressante consiste à un autre, de la même classe, mais à l’aide de Polly pour implémenter les mécanismes résilients que vous souhaitez utiliser le code, dans l’exemple suivant, effectue une nouvelle tentative avec interruption exponentielle.

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

Avec Polly, vous définissez une stratégie de nouvelle tentative avec le nombre de nouvelles tentatives, la configuration de l’interruption exponentielle et les actions à entreprendre lorsqu’il existe une exception HTTP, telles que la journalisation de l’erreur. Dans ce cas, la stratégie est configurée afin qu’il va tenter du nombre de fois spécifié lors de l’inscription des types dans le conteneur inversion de contrôle. En raison de la configuration de l’interruption exponentielle, chaque fois que le code détecte une exception HttpRequest, il retente la demande Http après un laps de temps qui augmente de façon exponentielle en fonction de la configuration de la stratégie.

La méthode importante est HttpInvoker, ce qui rend les requêtes HTTP tout au long de cette classe d’utilitaire. Que méthode interne s’exécute la requête HTTP avec \_policyWrapper.ExecuteAsync, qui prend en compte la stratégie de nouvelle tentative.

Dans eShopOnContainers vous spécifiez des stratégies de Polly lors de l’inscription des types au niveau du conteneur inversion de contrôle, comme dans le code suivant à partir de la [application web MVC est à le startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) classe.

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

Notez que les objets IHttpClient sont instanciés en tant que singleton au lieu de comme transitoire afin que les connexions TCP sont utilisées efficacement par le service et [un problème avec les sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) n’a pas lieu.

Cependant, le point important sur la résilience est que vous appliquez la stratégie Polly WaitAndRetryAsync dans ResilientHttpClientFactory dans la méthode CreateResilientHttpClient, comme indiqué dans le code suivant :

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
[Précédente] (implement-custom-http-call-retries-exponential-backoff.md) [suivant] (implémentez-circuit-analyseur lexical-pattern.md)
