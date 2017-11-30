---
title: "Implémentation du modèle de disjoncteur"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation du modèle de disjoncteur"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2a629e25a7565aaba156f68cf06d9a24b6c2b8b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="ceabe-104">Implémentation du modèle de disjoncteur</span><span class="sxs-lookup"><span data-stu-id="ceabe-104">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="ceabe-105">Comme indiqué précédemment, vous devez gérer les erreurs qui peuvent prendre un certain délai de récupération, comme peut se produire quand vous essayez de vous connecter à un service distant ou une ressource.</span><span class="sxs-lookup"><span data-stu-id="ceabe-105">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="ceabe-106">Gérer ce type d’erreur peut améliorer la stabilité et la résilience d’une application.</span><span class="sxs-lookup"><span data-stu-id="ceabe-106">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="ceabe-107">Dans un environnement distribué, les appels à des ressources distantes et des services peut échouer en raison d’erreurs temporaires, tels que les connexions réseau lentes et délais d’attente, ou si des ressources sont lentes ou sont temporairement indisponibles.</span><span class="sxs-lookup"><span data-stu-id="ceabe-107">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="ceabe-108">Ces erreurs généralement corrigent d’eux-mêmes après une courte période et une application robuste de cloud doit être préparée à les gérer à l’aide d’une stratégie, comme le modèle de nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="ceabe-108">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="ceabe-109">Toutefois, il peut également être situations où les erreurs sont en raison d’événements imprévus qui peuvent prendre beaucoup plus de temps à corriger.</span><span class="sxs-lookup"><span data-stu-id="ceabe-109">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="ceabe-110">Ces erreurs peuvent s’échelonner de gravité d’une perte partielle de connectivité à la défaillance complète d’un service.</span><span class="sxs-lookup"><span data-stu-id="ceabe-110">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="ceabe-111">Dans ces situations, il peut être inutile de l’application en permanence retenter une opération qui est vouée à l’échec.</span><span class="sxs-lookup"><span data-stu-id="ceabe-111">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="ceabe-112">Au lieu de cela, l’application doit être codée pour accepter que l’opération a échoué et de gérer l’échec en conséquence.</span><span class="sxs-lookup"><span data-stu-id="ceabe-112">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="ceabe-113">Modèle de disjoncteur a un objectif différent que le modèle de nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="ceabe-113">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="ceabe-114">Le modèle de nouvelle tentative permet à une application retenter une opération dans l’attente que l’opération de réussir.</span><span class="sxs-lookup"><span data-stu-id="ceabe-114">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="ceabe-115">Modèle de disjoncteur empêche une application d’effectuer une opération qui risque d’échouer.</span><span class="sxs-lookup"><span data-stu-id="ceabe-115">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="ceabe-116">Une application peut combiner ces deux modèles à l’aide du modèle de nouvelle tentative pour appeler une opération via un disjoncteur.</span><span class="sxs-lookup"><span data-stu-id="ceabe-116">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="ceabe-117">Toutefois, la logique de nouvelle tentative doit être sensible à toute exception retournée par le disjoncteur, et elle doit abandonner des nouvelles tentatives si le disjoncteur indique qu’une erreur n’est pas temporaire.</span><span class="sxs-lookup"><span data-stu-id="ceabe-117">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="ceabe-118">Implémentation d’un modèle de disjoncteur avec Polly</span><span class="sxs-lookup"><span data-stu-id="ceabe-118">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="ceabe-119">Comme lors de l’implémentation de nouvelles tentatives, l’approche recommandée pour les disjoncteurs consiste à tirer parti d’éprouvées bibliothèques .NET comme Polly.</span><span class="sxs-lookup"><span data-stu-id="ceabe-119">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="ceabe-120">L’application eShopOnContainers utilise la stratégie de disjoncteur Polly lors de l’implémentation de tentatives HTTP.</span><span class="sxs-lookup"><span data-stu-id="ceabe-120">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="ceabe-121">En fait, l’application applique les deux stratégies à la classe d’utilitaire ResilientHttpClient.</span><span class="sxs-lookup"><span data-stu-id="ceabe-121">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="ceabe-122">Chaque fois que vous utilisez un objet de type ResilientHttpClient pour les requêtes HTTP (d’eShopOnContainers), vous appliquerez ces deux stratégies, mais vous pouvez ajouter des stratégies supplémentaires, trop.</span><span class="sxs-lookup"><span data-stu-id="ceabe-122">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="ceabe-123">La seule différence ici au code utilisé pour les tentatives d’appel HTTP est le code où vous ajoutez la stratégie de disjoncteur à la liste des stratégies à utiliser, comme indiqué à la fin du code suivant :</span><span class="sxs-lookup"><span data-stu-id="ceabe-123">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
            // number of retries
            6,
            // exponential backofff
            retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
            // on retry
            (exception, timeSpan, retryCount, context) =>
            {
                var msg = $"Retry {retryCount} implemented with Polly RetryPolicy " +
                    $"of {context.PolicyKey} " +
                    $"at {context.ExecutionKey}, " +
                    $"due to: {exception}.";
                _logger.LogWarning(msg);
                _logger.LogDebug(msg);
            }),
            Policy.Handle<HttpRequestException>()
                .CircuitBreakerAsync(
                    // number of exceptions before breaking circuit
                    5,
                    // time circuit opened before retry
                    TimeSpan.FromMinutes(1),
                    (exception, duration) =>
                    {
                        // on circuit opened
                        _logger.LogTrace("Circuit breaker opened");
                    },
                    () =>
                    {
                        // on circuit closed
                        _logger.LogTrace("Circuit breaker reset");
                    })
    };
}
```

<span data-ttu-id="ceabe-124">Le code ajoute une stratégie pour le wrapper HTTP.</span><span class="sxs-lookup"><span data-stu-id="ceabe-124">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="ceabe-125">Que stratégie définit un disjoncteur qui s’ouvre lorsque le code détecte le nombre spécifié d’exceptions consécutifs (exceptions dans une ligne), en tant que passé dans le paramètre exceptionsAllowedBeforeBreaking (5 dans ce cas).</span><span class="sxs-lookup"><span data-stu-id="ceabe-125">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="ceabe-126">Lorsque le circuit est ouvert, les requêtes HTTP ne fonctionnent pas, mais une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="ceabe-126">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="ceabe-127">Les disjoncteurs doit également être utilisées pour rediriger les demandes vers une infrastructure de secours si vous pouvez rencontrer des problèmes dans une ressource particulière qui est déployé dans un environnement autre que l’application cliente ou d’un service qui effectue l’appel HTTP.</span><span class="sxs-lookup"><span data-stu-id="ceabe-127">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="ceabe-128">De cette façon, s’il existe une panne du centre de données qui a un impact sur uniquement votre microservices principal, mais pas les applications clientes, les applications clientes peuvent rediriger vers les services de secours.</span><span class="sxs-lookup"><span data-stu-id="ceabe-128">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="ceabe-129">Polly projette une nouvelle stratégie pour automatiser ce processus [stratégie de basculement](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scénario.</span><span class="sxs-lookup"><span data-stu-id="ceabe-129">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="ceabe-130">Bien entendu, toutes ces fonctionnalités sont pour les cas où vous gérez le basculement depuis le code .NET, au lieu qu’il est géré automatiquement par Azure, avec la transparence de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="ceabe-130">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="ceabe-131">À l’aide de la classe utilitaire ResilientHttpClient eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="ceabe-131">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="ceabe-132">Vous utilisez la classe d’utilitaire ResilientHttpClient de manière similaire à l’utilisation de la classe .NET HttpClient.</span><span class="sxs-lookup"><span data-stu-id="ceabe-132">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="ceabe-133">Dans l’exemple suivant à partir de l’application de web MVC eShopOnContainers (la classe de l’agent OrderingService utilisée par OrderController), l’objet ResilientHttpClient est injecté par le paramètre httpClient du constructeur.</span><span class="sxs-lookup"><span data-stu-id="ceabe-133">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="ceabe-134">Puis, l’objet est utilisé pour effectuer des requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="ceabe-134">Then the object is used to perform HTTP requests.</span></span>

```csharp
public class OrderingService : IOrderingService
{
    private IHttpClient _apiClient;
    private readonly string _remoteServiceBaseUrl;
    private readonly IOptionsSnapshot<AppSettings> _settings;
    private readonly IHttpContextAccessor _httpContextAccesor;

    public OrderingService(IOptionsSnapshot<AppSettings> settings,
        IHttpContextAccessor httpContextAccesor,
        IHttpClient httpClient)
    {
        _remoteServiceBaseUrl = $"{settings.Value.OrderingUrl}/api/v1/orders";
        _settings = settings;
        _httpContextAccesor = httpContextAccesor;
        _apiClient = httpClient;
    }

    async public Task<List<Order>> GetMyOrders(ApplicationUser user)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        var ordersUrl = _remoteServiceBaseUrl;
        var dataString = await _apiClient.GetStringAsync(ordersUrl);
        var response = JsonConvert.DeserializeObject<List<Order>>(dataString);
        return response;
    }

    // Other methods ...
    async public Task CreateOrder(Order order)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        _apiClient.Inst.DefaultRequestHeaders.Add("x-requestid",
            order.RequestId.ToString());
        var ordersUrl = $"{_remoteServiceBaseUrl}/new";
        order.CardTypeId = 1;
        order.CardExpirationApiFormat();
        SetFakeIdToProducts(order);
        var response = await _apiClient.PostAsync(ordersUrl, order);
        response.EnsureSuccessStatusCode();
    }
}
```

<span data-ttu-id="ceabe-135">Chaque fois que le \_apiClient membre objet est utilisé, il utilise en interne la classe wrapper avec Polly policiesؙ : la stratégie de nouvelle tentative, la stratégie de disjoncteur et toute autre stratégie que vous pouvez appliquer à partir de la collection de stratégies Polly.</span><span class="sxs-lookup"><span data-stu-id="ceabe-135">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="ceabe-136">Tester les nouvelles tentatives dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="ceabe-136">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="ceabe-137">Chaque fois que vous démarrez la solution eShopOnContainers dans un hôte Docker, il doit démarrer plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="ceabe-137">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="ceabe-138">Certains des conteneurs sont plus lents à démarrer et initialiser, comme le conteneur de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ceabe-138">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="ceabe-139">Cela est particulièrement vrai la première fois que vous déployez l’application eShopOnContainers dans Docker, car il a besoin installer les images et la base de données.</span><span class="sxs-lookup"><span data-stu-id="ceabe-139">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="ceabe-140">Le fait que certains conteneurs démarrent plus lentement que d’autres utilisateurs peuvent entraîner le reste des services à initialement lever des exceptions HTTP, même si vous définissez des dépendances entre les conteneurs au composer docker niveau, comme expliqué dans les sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="ceabe-140">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="ceabe-141">Ceux docker-composent des dépendances entre les conteneurs sont uniquement au niveau du processus.</span><span class="sxs-lookup"><span data-stu-id="ceabe-141">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="ceabe-142">Le processus de point d’entrée du conteneur peut être démarré, mais SQL Server n’est peut-être pas prêt pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="ceabe-142">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="ceabe-143">Le résultat peut être en cascade d’erreurs, et l’application peut obtenir une exception lorsque vous tentez d’utiliser ce conteneur particulier.</span><span class="sxs-lookup"><span data-stu-id="ceabe-143">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="ceabe-144">Vous pouvez également voir ce type d’erreur au démarrage lorsque le déploie de l’application dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="ceabe-144">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="ceabe-145">Dans ce cas, orchestrators peut déplacer conteneurs d’un nœud ou une machine virtuelle à un autre (qui est, à partir de nouvelles instances) lors de l’équilibrage de charge le nombre de conteneurs entre les nœuds du cluster.</span><span class="sxs-lookup"><span data-stu-id="ceabe-145">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="ceabe-146">L’eShopOnContainers résout ce problème consiste à l’aide du modèle de nouvelle tentative que nous indiqués plus haut.</span><span class="sxs-lookup"><span data-stu-id="ceabe-146">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="ceabe-147">Il est également pourquoi, lors du démarrage de la solution, vous pouvez obtenir les traces de journal ou d’avertissements à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ceabe-147">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="ceabe-148">«**Nouvelle tentative 1 implémentée avec RetryPolicy de Polly**, en raison : System.Net.Http.HttpRequestException : une erreur s’est produite lors de l’envoi de la demande.</span><span class="sxs-lookup"><span data-stu-id="ceabe-148">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="ceabe-149"> ---&gt;System.Net.Http.CurlException : Impossible de se connecter au serveur\\n en System.Net.Http.CurlHandler.ThrowIfCURLEError (erreur CURLcode)\\n en \[... \].</span><span class="sxs-lookup"><span data-stu-id="ceabe-149"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="ceabe-150">Tester le disjoncteur dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="ceabe-150">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="ceabe-151">Il existe plusieurs façons, vous pouvez ouvrir le circuit et testez-le avec eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ceabe-151">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="ceabe-152">Une option consiste à réduire le nombre autorisé de tentatives de 1 dans la stratégie de disjoncteur et de redéployer la solution dans son intégralité dans Docker.</span><span class="sxs-lookup"><span data-stu-id="ceabe-152">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="ceabe-153">Avec une nouvelle tentative unique, il est également possible qu’une requête HTTP échoue pendant le déploiement, le disjoncteur s’ouvre et vous obtenez une erreur.</span><span class="sxs-lookup"><span data-stu-id="ceabe-153">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="ceabe-154">Une autre option consiste à utiliser l’intergiciel (middleware) personnalisé qui est implémenté dans l’ordre de tri microservice.</span><span class="sxs-lookup"><span data-stu-id="ceabe-154">Another option is to use custom middleware that is implemented in the ordering microservice.</span></span> <span data-ttu-id="ceabe-155">Lorsque cet intergiciel (middleware) est activée, elle intercepte toutes les demandes HTTP et renvoie le code d’état 500.</span><span class="sxs-lookup"><span data-stu-id="ceabe-155">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="ceabe-156">Vous pouvez activer l’intergiciel (middleware) en effectuant une requête GET à l’échec d’URI, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ceabe-156">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="ceabe-157">OBTENIR/défaillant</span><span class="sxs-lookup"><span data-stu-id="ceabe-157">GET /failing</span></span>

<span data-ttu-id="ceabe-158">Cette requête retourne l’état actuel de l’intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="ceabe-158">This request returns the current state of the middleware.</span></span> <span data-ttu-id="ceabe-159">Si l’intergiciel (middleware) est activé, la requête retourne de code d’état 500.</span><span class="sxs-lookup"><span data-stu-id="ceabe-159">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="ceabe-160">Si l’intergiciel (middleware) est désactivé, il n’existe aucune réponse.</span><span class="sxs-lookup"><span data-stu-id="ceabe-160">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="ceabe-161">OBTENIR/défaillant ? activer</span><span class="sxs-lookup"><span data-stu-id="ceabe-161">GET /failing?enable</span></span>

<span data-ttu-id="ceabe-162">Cette requête permet de l’intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="ceabe-162">This request enables the middleware.</span></span>

-   <span data-ttu-id="ceabe-163">OBTENIR/défaillant ? désactiver</span><span class="sxs-lookup"><span data-stu-id="ceabe-163">GET /failing?disable</span></span>

<span data-ttu-id="ceabe-164">Cette demande désactive l’intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="ceabe-164">This request disables the middleware.</span></span>

<span data-ttu-id="ceabe-165">Par exemple, une fois que l’application est en cours d’exécution, vous pouvez activer l’intergiciel (middleware) en faisant une demande à l’aide de l’URI suivant dans n’importe quel navigateur.</span><span class="sxs-lookup"><span data-stu-id="ceabe-165">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="ceabe-166">Notez que le tri microservice utilise le port 5102.</span><span class="sxs-lookup"><span data-stu-id="ceabe-166">Note that the ordering microservice uses port 5102.</span></span>

<span data-ttu-id="ceabe-167">http://localhost:5102 / défaillant ? activer</span><span class="sxs-lookup"><span data-stu-id="ceabe-167">http://localhost:5102/failing?enable</span></span>

<span data-ttu-id="ceabe-168">Vous pouvez vérifier puis de l’état à l’aide de l’URI [http://localhost:5102 / défaillant](http://localhost:5100/failing), comme illustré dans la Figure 10-4.</span><span class="sxs-lookup"><span data-stu-id="ceabe-168">You can then check the status using the URI [http://localhost:5102/failing](http://localhost:5100/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="ceabe-169">**Figure 10-4**.</span><span class="sxs-lookup"><span data-stu-id="ceabe-169">**Figure 10-4**.</span></span> <span data-ttu-id="ceabe-170">Simulation d’un échec avec l’intergiciel (middleware) ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ceabe-170">Simulating a failure with ASP.NET middleware</span></span>

<span data-ttu-id="ceabe-171">À ce stade, le classement répond de microservice avec le code d’état 500 chaque fois que vous appelez l’appeler.</span><span class="sxs-lookup"><span data-stu-id="ceabe-171">At this point, the ordering microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="ceabe-172">Une fois que l’intergiciel (middleware) est en cours d’exécution, vous pouvez essayer d’effectuer une commande à partir de l’application web MVC.</span><span class="sxs-lookup"><span data-stu-id="ceabe-172">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="ceabe-173">Étant donné que les requêtes échoue, le circuit s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="ceabe-173">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="ceabe-174">Dans l’exemple suivant, vous pouvez voir que l’application web MVC a un bloc catch bloquer dans la logique de passer une commande.</span><span class="sxs-lookup"><span data-stu-id="ceabe-174">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="ceabe-175">Si le code intercepte une exception de circuit ouvert, il affiche l’utilisateur un message convivial les invitant à attendre.</span><span class="sxs-lookup"><span data-stu-id="ceabe-175">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
[HttpPost]
public async Task<IActionResult> Create(Order model, string action)
{
    try
    {
        if (ModelState.IsValid)
        {
            var user = _appUserParser.Parse(HttpContext.User);
            await _orderSvc.CreateOrder(model);
            //Redirect to historic list.
            return RedirectToAction("Index");
        }
    }
    catch(BrokenCircuitException ex)
    {
        ModelState.AddModelError("Error",
            "It was not possible to create a new order, please try later on");
    }
    return View(model);
}
```

<span data-ttu-id="ceabe-176">Voici un résumé.</span><span class="sxs-lookup"><span data-stu-id="ceabe-176">Here’s a summary.</span></span> <span data-ttu-id="ceabe-177">La stratégie de nouvelle tentative tente plusieurs fois pour créer la requête HTTP et obtient les erreurs HTTP.</span><span class="sxs-lookup"><span data-stu-id="ceabe-177">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="ceabe-178">Lorsque le nombre de tentatives atteint le nombre maximal défini pour la stratégie de disjoncteur (dans ce cas, 5), l’application lève une BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="ceabe-178">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="ceabe-179">Le résultat est un message convivial, comme indiqué dans la Figure 10-5.</span><span class="sxs-lookup"><span data-stu-id="ceabe-179">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="ceabe-180">**Figure 10-5**.</span><span class="sxs-lookup"><span data-stu-id="ceabe-180">**Figure 10-5**.</span></span> <span data-ttu-id="ceabe-181">Disjoncteur renvoyant une erreur à l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="ceabe-181">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="ceabe-182">Vous pouvez implémenter une logique différente pour l’ouvrir le circuit.</span><span class="sxs-lookup"><span data-stu-id="ceabe-182">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="ceabe-183">Ou bien, vous pouvez essayer une requête HTTP sur un microservice principaux différents s’il existe un centre de données de secours ou un système principal redondant.</span><span class="sxs-lookup"><span data-stu-id="ceabe-183">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="ceabe-184">Enfin, une autre possibilité pour le CircuitBreakerPolicy consiste à utiliser isolent (qui force l’ouvrir et maintient ouvert le circuit) et réinitialisation (qui se ferme à nouveau).</span><span class="sxs-lookup"><span data-stu-id="ceabe-184">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="ceabe-185">Il peut servir à créer un point de terminaison HTTP utilitaire appelle isoler et réinitialisation directement sur la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ceabe-185">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="ceabe-186">Ce point de terminaison HTTP peut également servir, convenablement sécurisés, en production d’isolement temporaire d’un système en aval, par exemple lorsque vous souhaitez mettre à niveau.</span><span class="sxs-lookup"><span data-stu-id="ceabe-186">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="ceabe-187">Ou bien il peut déclencher le circuit manuellement pour protéger un système en aval que vous soupçonnez d’être défaillant.</span><span class="sxs-lookup"><span data-stu-id="ceabe-187">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="ceabe-188">Ajout d’une stratégie d’instabilité à la stratégie de nouvelle tentative</span><span class="sxs-lookup"><span data-stu-id="ceabe-188">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="ceabe-189">Stratégie de nouvelle tentative régulière peut affecter votre système en cas d’évolutivité et haute simultanéité et sous une contention élevée.</span><span class="sxs-lookup"><span data-stu-id="ceabe-189">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="ceabe-190">Pour éviter des pics de tentatives similaires provenant d’un grand nombre de clients en cas de pannes partielles, une bonne solution de contournement est pour ajouter une stratégie d’instabilité pour l’algorithme/stratégie de nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="ceabe-190">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="ceabe-191">Cela peut améliorer les performances globales du système de bout en bout en ajoutant le caractère aléatoire pour l’interruption exponentielle.</span><span class="sxs-lookup"><span data-stu-id="ceabe-191">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="ceabe-192">Cela permet de répartir les pointes lorsque des problèmes surviennent.</span><span class="sxs-lookup"><span data-stu-id="ceabe-192">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="ceabe-193">Lorsque vous utilisez Polly, code d’implémentation instabilité pourrait ressembler à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ceabe-193">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="ceabe-194">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="ceabe-194">Additional resources</span></span>

-   <span data-ttu-id="ceabe-195">**Recommencez modèle**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="ceabe-195">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="ceabe-196">**Résilience des connexions** (Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="ceabe-196">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="ceabe-197">**Polly** (bibliothèque de gestion d’erreurs transitoires et résilience de .NET) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="ceabe-197">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="ceabe-198">**Modèle de disjoncteur**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="ceabe-198">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="ceabe-199">**Goff de Marc. Instabilité : Rendre les choses mieux avec caractère aléatoire** https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="ceabe-199">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ceabe-200">[Précédente] (implement-http-call-retries-exponential-backoff-polly.md) [suivant] (analyse-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="ceabe-200">[Previous] (implement-http-call-retries-exponential-backoff-polly.md) [Next] (monitor-app-health.md)</span></span>
