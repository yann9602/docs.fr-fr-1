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
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a>Implémentation de connexions d’Entity Framework Core SQL résilientes

Pour la base de données SQL Azure, Entity Framework Core fournit déjà la logique de résilience et de nouvelle tentative de connexion de base de données interne. Mais vous devez activer la stratégie de l’exécution d’Entity Framework pour chaque connexion DbContext si vous souhaitez avoir [des connexions EF Core résilientes](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).

Par exemple, le code suivant au niveau de la connexion EF Core permet des connexions SQL résilientes qui sont retentées si la connexion échoue.

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Stratégies d’exécution et les transactions explicites à l’aide de BeginTransaction et plusieurs DbContexts

Lorsque de nouvelles tentatives sont activées dans les connexions EF Core, chaque opération que vous effectuez à l’aide de EF Core devient son propre opération reproductible. Chaque requête et chaque appel à SaveChanges va être retentées en tant qu’unité si une défaillance temporaire se produit.

Toutefois, si votre code initie une transaction à l’aide de BeginTransaction, vous définissez votre propre groupe d’opérations qui doivent être traités en tant qu’unité, tous les éléments à l’intérieur de la transaction est restaurée si une défaillance se produit. Une exception à ce qui suit s’affiche si vous tentez d’exécuter cette transaction lors de l’utilisation d’une stratégie d’exécution EF (stratégie de nouvelle tentative) et que vous incluez plusieurs appels SaveChanges à partir de plusieurs DbContexts dans la transaction.

> System.InvalidOperationException : La stratégie d’exécution configurée 'SqlServerRetryingExecutionStrategy' ne prend pas en charge les transactions démarrées par l’utilisateur. Utilisez la stratégie d’exécution retournée par 'DbContext.Database.CreateExecutionStrategy()' pour exécuter toutes les opérations dans la transaction comme une unité reproductible.

La solution consiste à appeler manuellement la stratégie d’exécution EF avec un délégué qui représente tous les éléments qui doit être exécutée. Si une défaillance temporaire se produit, la stratégie d’exécution appelle le délégué à nouveau. Par exemple, le code suivant montre comment il est implémenté dans eShopOnContainers avec deux DbContexts plusieurs (\_catalogContext et le IntegrationEventLogContext) lors de la mise à jour d’un produit et l’enregistrement puis le Objet ProductPriceChangedIntegrationEvent qui a besoin d’utiliser un autre DbContext.

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

Le premier DbContext est \_catalogContext et le second DbContext se trouve dans le \_integrationEventLogService objet. L’action de validation est effectuée entre plusieurs DbContexts à l’aide d’une stratégie d’exécution EF.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Résilience des connexions et l’Interception de commande avec Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesar de la Torre. À l’aide de résilient Entity Framework Core Sql connexions et Transactions**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>


>[!div class="step-by-step"]
[Précédente] (mettre en œuvre-tentatives-exponentielle-backoff.md) [suivant] (implement-custom-http-call-retries-exponential-backoff.md)
