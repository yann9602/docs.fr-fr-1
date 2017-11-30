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
# <a name="implementing-the-circuit-breaker-pattern"></a>Implémentation du modèle de disjoncteur

Comme indiqué précédemment, vous devez gérer les erreurs qui peuvent prendre un certain délai de récupération, comme peut se produire quand vous essayez de vous connecter à un service distant ou une ressource. Gérer ce type d’erreur peut améliorer la stabilité et la résilience d’une application.

Dans un environnement distribué, les appels à des ressources distantes et des services peut échouer en raison d’erreurs temporaires, tels que les connexions réseau lentes et délais d’attente, ou si des ressources sont lentes ou sont temporairement indisponibles. Ces erreurs généralement corrigent d’eux-mêmes après une courte période et une application robuste de cloud doit être préparée à les gérer à l’aide d’une stratégie, comme le modèle de nouvelle tentative.

Toutefois, il peut également être situations où les erreurs sont en raison d’événements imprévus qui peuvent prendre beaucoup plus de temps à corriger. Ces erreurs peuvent s’échelonner de gravité d’une perte partielle de connectivité à la défaillance complète d’un service. Dans ces situations, il peut être inutile de l’application en permanence retenter une opération qui est vouée à l’échec. Au lieu de cela, l’application doit être codée pour accepter que l’opération a échoué et de gérer l’échec en conséquence.

Modèle de disjoncteur a un objectif différent que le modèle de nouvelle tentative. Le modèle de nouvelle tentative permet à une application retenter une opération dans l’attente que l’opération de réussir. Modèle de disjoncteur empêche une application d’effectuer une opération qui risque d’échouer. Une application peut combiner ces deux modèles à l’aide du modèle de nouvelle tentative pour appeler une opération via un disjoncteur. Toutefois, la logique de nouvelle tentative doit être sensible à toute exception retournée par le disjoncteur, et elle doit abandonner des nouvelles tentatives si le disjoncteur indique qu’une erreur n’est pas temporaire.

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>Implémentation d’un modèle de disjoncteur avec Polly

Comme lors de l’implémentation de nouvelles tentatives, l’approche recommandée pour les disjoncteurs consiste à tirer parti d’éprouvées bibliothèques .NET comme Polly.

L’application eShopOnContainers utilise la stratégie de disjoncteur Polly lors de l’implémentation de tentatives HTTP. En fait, l’application applique les deux stratégies à la classe d’utilitaire ResilientHttpClient. Chaque fois que vous utilisez un objet de type ResilientHttpClient pour les requêtes HTTP (d’eShopOnContainers), vous appliquerez ces deux stratégies, mais vous pouvez ajouter des stratégies supplémentaires, trop.

La seule différence ici au code utilisé pour les tentatives d’appel HTTP est le code où vous ajoutez la stratégie de disjoncteur à la liste des stratégies à utiliser, comme indiqué à la fin du code suivant :

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

Le code ajoute une stratégie pour le wrapper HTTP. Que stratégie définit un disjoncteur qui s’ouvre lorsque le code détecte le nombre spécifié d’exceptions consécutifs (exceptions dans une ligne), en tant que passé dans le paramètre exceptionsAllowedBeforeBreaking (5 dans ce cas). Lorsque le circuit est ouvert, les requêtes HTTP ne fonctionnent pas, mais une exception est levée.

Les disjoncteurs doit également être utilisées pour rediriger les demandes vers une infrastructure de secours si vous pouvez rencontrer des problèmes dans une ressource particulière qui est déployé dans un environnement autre que l’application cliente ou d’un service qui effectue l’appel HTTP. De cette façon, s’il existe une panne du centre de données qui a un impact sur uniquement votre microservices principal, mais pas les applications clientes, les applications clientes peuvent rediriger vers les services de secours. Polly projette une nouvelle stratégie pour automatiser ce processus [stratégie de basculement](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scénario.

Bien entendu, toutes ces fonctionnalités sont pour les cas où vous gérez le basculement depuis le code .NET, au lieu qu’il est géré automatiquement par Azure, avec la transparence de l’emplacement.

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>À l’aide de la classe utilitaire ResilientHttpClient eShopOnContainers

Vous utilisez la classe d’utilitaire ResilientHttpClient de manière similaire à l’utilisation de la classe .NET HttpClient. Dans l’exemple suivant à partir de l’application de web MVC eShopOnContainers (la classe de l’agent OrderingService utilisée par OrderController), l’objet ResilientHttpClient est injecté par le paramètre httpClient du constructeur. Puis, l’objet est utilisé pour effectuer des requêtes HTTP.

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

Chaque fois que le \_apiClient membre objet est utilisé, il utilise en interne la classe wrapper avec Polly policiesؙ : la stratégie de nouvelle tentative, la stratégie de disjoncteur et toute autre stratégie que vous pouvez appliquer à partir de la collection de stratégies Polly.

## <a name="testing-retries-in-eshoponcontainers"></a>Tester les nouvelles tentatives dans eShopOnContainers

Chaque fois que vous démarrez la solution eShopOnContainers dans un hôte Docker, il doit démarrer plusieurs conteneurs. Certains des conteneurs sont plus lents à démarrer et initialiser, comme le conteneur de SQL Server. Cela est particulièrement vrai la première fois que vous déployez l’application eShopOnContainers dans Docker, car il a besoin installer les images et la base de données. Le fait que certains conteneurs démarrent plus lentement que d’autres utilisateurs peuvent entraîner le reste des services à initialement lever des exceptions HTTP, même si vous définissez des dépendances entre les conteneurs au composer docker niveau, comme expliqué dans les sections précédentes. Ceux docker-composent des dépendances entre les conteneurs sont uniquement au niveau du processus. Le processus de point d’entrée du conteneur peut être démarré, mais SQL Server n’est peut-être pas prêt pour les requêtes. Le résultat peut être en cascade d’erreurs, et l’application peut obtenir une exception lorsque vous tentez d’utiliser ce conteneur particulier.

Vous pouvez également voir ce type d’erreur au démarrage lorsque le déploie de l’application dans le cloud. Dans ce cas, orchestrators peut déplacer conteneurs d’un nœud ou une machine virtuelle à un autre (qui est, à partir de nouvelles instances) lors de l’équilibrage de charge le nombre de conteneurs entre les nœuds du cluster.

L’eShopOnContainers résout ce problème consiste à l’aide du modèle de nouvelle tentative que nous indiqués plus haut. Il est également pourquoi, lors du démarrage de la solution, vous pouvez obtenir les traces de journal ou d’avertissements à ce qui suit :

> «**Nouvelle tentative 1 implémentée avec RetryPolicy de Polly**, en raison : System.Net.Http.HttpRequestException : une erreur s’est produite lors de l’envoi de la demande. ---&gt;System.Net.Http.CurlException : Impossible de se connecter au serveur\\n en System.Net.Http.CurlHandler.ThrowIfCURLEError (erreur CURLcode)\\n en \[... \].

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>Tester le disjoncteur dans eShopOnContainers

Il existe plusieurs façons, vous pouvez ouvrir le circuit et testez-le avec eShopOnContainers.

Une option consiste à réduire le nombre autorisé de tentatives de 1 dans la stratégie de disjoncteur et de redéployer la solution dans son intégralité dans Docker. Avec une nouvelle tentative unique, il est également possible qu’une requête HTTP échoue pendant le déploiement, le disjoncteur s’ouvre et vous obtenez une erreur.

Une autre option consiste à utiliser l’intergiciel (middleware) personnalisé qui est implémenté dans l’ordre de tri microservice. Lorsque cet intergiciel (middleware) est activée, elle intercepte toutes les demandes HTTP et renvoie le code d’état 500. Vous pouvez activer l’intergiciel (middleware) en effectuant une requête GET à l’échec d’URI, comme suit :

-   OBTENIR/défaillant

Cette requête retourne l’état actuel de l’intergiciel (middleware). Si l’intergiciel (middleware) est activé, la requête retourne de code d’état 500. Si l’intergiciel (middleware) est désactivé, il n’existe aucune réponse.

-   OBTENIR/défaillant ? activer

Cette requête permet de l’intergiciel (middleware).

-   OBTENIR/défaillant ? désactiver

Cette demande désactive l’intergiciel (middleware).

Par exemple, une fois que l’application est en cours d’exécution, vous pouvez activer l’intergiciel (middleware) en faisant une demande à l’aide de l’URI suivant dans n’importe quel navigateur. Notez que le tri microservice utilise le port 5102.

http://localhost:5102 / défaillant ? activer

Vous pouvez vérifier puis de l’état à l’aide de l’URI [http://localhost:5102 / défaillant](http://localhost:5100/failing), comme illustré dans la Figure 10-4.

![](./media/image4.png)

**Figure 10-4**. Simulation d’un échec avec l’intergiciel (middleware) ASP.NET

À ce stade, le classement répond de microservice avec le code d’état 500 chaque fois que vous appelez l’appeler.

Une fois que l’intergiciel (middleware) est en cours d’exécution, vous pouvez essayer d’effectuer une commande à partir de l’application web MVC. Étant donné que les requêtes échoue, le circuit s’ouvre.

Dans l’exemple suivant, vous pouvez voir que l’application web MVC a un bloc catch bloquer dans la logique de passer une commande. Si le code intercepte une exception de circuit ouvert, il affiche l’utilisateur un message convivial les invitant à attendre.

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

Voici un résumé. La stratégie de nouvelle tentative tente plusieurs fois pour créer la requête HTTP et obtient les erreurs HTTP. Lorsque le nombre de tentatives atteint le nombre maximal défini pour la stratégie de disjoncteur (dans ce cas, 5), l’application lève une BrokenCircuitException. Le résultat est un message convivial, comme indiqué dans la Figure 10-5.

![](./media/image5.png)

**Figure 10-5**. Disjoncteur renvoyant une erreur à l’interface utilisateur

Vous pouvez implémenter une logique différente pour l’ouvrir le circuit. Ou bien, vous pouvez essayer une requête HTTP sur un microservice principaux différents s’il existe un centre de données de secours ou un système principal redondant.

Enfin, une autre possibilité pour le CircuitBreakerPolicy consiste à utiliser isolent (qui force l’ouvrir et maintient ouvert le circuit) et réinitialisation (qui se ferme à nouveau). Il peut servir à créer un point de terminaison HTTP utilitaire appelle isoler et réinitialisation directement sur la stratégie. Ce point de terminaison HTTP peut également servir, convenablement sécurisés, en production d’isolement temporaire d’un système en aval, par exemple lorsque vous souhaitez mettre à niveau. Ou bien il peut déclencher le circuit manuellement pour protéger un système en aval que vous soupçonnez d’être défaillant.

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>Ajout d’une stratégie d’instabilité à la stratégie de nouvelle tentative

Stratégie de nouvelle tentative régulière peut affecter votre système en cas d’évolutivité et haute simultanéité et sous une contention élevée. Pour éviter des pics de tentatives similaires provenant d’un grand nombre de clients en cas de pannes partielles, une bonne solution de contournement est pour ajouter une stratégie d’instabilité pour l’algorithme/stratégie de nouvelle tentative. Cela peut améliorer les performances globales du système de bout en bout en ajoutant le caractère aléatoire pour l’interruption exponentielle. Cela permet de répartir les pointes lorsque des problèmes surviennent. Lorsque vous utilisez Polly, code d’implémentation instabilité pourrait ressembler à l’exemple suivant :

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Recommencez modèle**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **Résilience des connexions** (Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Polly** (bibliothèque de gestion d’erreurs transitoires et résilience de .NET) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **Modèle de disjoncteur**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Goff de Marc. Instabilité : Rendre les choses mieux avec caractère aléatoire** https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[Précédente] (implement-http-call-retries-exponential-backoff-polly.md) [suivant] (analyse-app-health.md)
