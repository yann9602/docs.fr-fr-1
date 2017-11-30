---
title: "Implémentation de connexions d’Entity Framework Core SQL résilientes"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation de connexions d’Entity Framework Core SQL résilientes"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 8600625c2022d69ebaa2645c2a8159a848b12ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="59ee4-104">Implémentation de connexions d’Entity Framework Core SQL résilientes</span><span class="sxs-lookup"><span data-stu-id="59ee4-104">Implementing resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="59ee4-105">Pour la base de données SQL Azure, Entity Framework Core fournit déjà la logique de résilience et de nouvelle tentative de connexion de base de données interne.</span><span class="sxs-lookup"><span data-stu-id="59ee4-105">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="59ee4-106">Mais vous devez activer la stratégie de l’exécution d’Entity Framework pour chaque connexion DbContext si vous souhaitez avoir [des connexions EF Core résilientes](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="59ee4-106">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="59ee4-107">Par exemple, le code suivant au niveau de la connexion EF Core permet des connexions SQL résilientes qui sont retentées si la connexion échoue.</span><span class="sxs-lookup"><span data-stu-id="59ee4-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 5,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="59ee4-108">Stratégies d’exécution et les transactions explicites à l’aide de BeginTransaction et plusieurs DbContexts</span><span class="sxs-lookup"><span data-stu-id="59ee4-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="59ee4-109">Lorsque de nouvelles tentatives sont activées dans les connexions EF Core, chaque opération que vous effectuez à l’aide de EF Core devient son propre opération reproductible.</span><span class="sxs-lookup"><span data-stu-id="59ee4-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="59ee4-110">Chaque requête et chaque appel à SaveChanges va être retentées en tant qu’unité si une défaillance temporaire se produit.</span><span class="sxs-lookup"><span data-stu-id="59ee4-110">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="59ee4-111">Toutefois, si votre code initie une transaction à l’aide de BeginTransaction, vous définissez votre propre groupe d’opérations qui doivent être traités en tant qu’unité, tous les éléments à l’intérieur de la transaction est restaurée si une défaillance se produit.</span><span class="sxs-lookup"><span data-stu-id="59ee4-111">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="59ee4-112">Une exception à ce qui suit s’affiche si vous tentez d’exécuter cette transaction lors de l’utilisation d’une stratégie d’exécution EF (stratégie de nouvelle tentative) et que vous incluez plusieurs appels SaveChanges à partir de plusieurs DbContexts dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="59ee4-112">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="59ee4-113">System.InvalidOperationException : La stratégie d’exécution configurée 'SqlServerRetryingExecutionStrategy' ne prend pas en charge les transactions démarrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="59ee4-113">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="59ee4-114">Utilisez la stratégie d’exécution retournée par 'DbContext.Database.CreateExecutionStrategy()' pour exécuter toutes les opérations dans la transaction comme une unité reproductible.</span><span class="sxs-lookup"><span data-stu-id="59ee4-114">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="59ee4-115">La solution consiste à appeler manuellement la stratégie d’exécution EF avec un délégué qui représente tous les éléments qui doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="59ee4-115">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="59ee4-116">Si une défaillance temporaire se produit, la stratégie d’exécution appelle le délégué à nouveau.</span><span class="sxs-lookup"><span data-stu-id="59ee4-116">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="59ee4-117">Par exemple, le code suivant montre comment il est implémenté dans eShopOnContainers avec deux DbContexts plusieurs (\_catalogContext et le IntegrationEventLogContext) lors de la mise à jour d’un produit et l’enregistrement puis le Objet ProductPriceChangedIntegrationEvent qui a besoin d’utiliser un autre DbContext.</span><span class="sxs-lookup"><span data-stu-id="59ee4-117">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

```csharp
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem
    productToUpdate)
{
    // Other code ...
    // Update current product
    catalogItem = productToUpdate;

    // Use of an EF Core resiliency strategy when using multiple DbContexts
    // within an explicit transaction
    // See:
    // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
    var strategy = _catalogContext.Database.CreateExecutionStrategy();
    await strategy.ExecuteAsync(async () =>
    {
        // Achieving atomicity between original Catalog database operation and the
        // IntegrationEventLog thanks to a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
            _catalogContext.CatalogItems.Update(catalogItem);
            await _catalogContext.SaveChangesAsync();
            // Save to EventLog only if product price changed
            if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
            transaction.Commit();
        }
    });
}
```

<span data-ttu-id="59ee4-118">Le premier DbContext est \_catalogContext et le second DbContext se trouve dans le \_integrationEventLogService objet.</span><span class="sxs-lookup"><span data-stu-id="59ee4-118">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="59ee4-119">L’action de validation est effectuée entre plusieurs DbContexts à l’aide d’une stratégie d’exécution EF.</span><span class="sxs-lookup"><span data-stu-id="59ee4-119">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="59ee4-120">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="59ee4-120">Additional resources</span></span>

-   <span data-ttu-id="59ee4-121">**Résilience des connexions et l’Interception de commande avec Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="59ee4-121">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="59ee4-122">**Cesar de la Torre. À l’aide de résilient Entity Framework Core Sql connexions et Transactions**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="59ee4-122">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="59ee4-123">[Précédente] (mettre en œuvre-tentatives-exponentielle-backoff.md) [suivant] (implement-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="59ee4-123">[Previous] (implement-retries-exponential-backoff.md) [Next] (implement-custom-http-call-retries-exponential-backoff.md)</span></span>
