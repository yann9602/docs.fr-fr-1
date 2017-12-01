---
title: "À l’aide de bases de données NoSQL comme une infrastructure de persistance"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | À l’aide de bases de données NoSQL comme une infrastructure de persistance"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e4b63511069b89cc5761ce7ed64f09e9035a56a3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a>À l’aide de bases de données NoSQL comme une infrastructure de persistance

Lorsque vous utilisez des bases de données NoSQL pour votre couche de données d’infrastructure, vous n’utilisez généralement pas un ORM comme Entity Framework Core. Au lieu de cela, vous utilisez l’API fournie par le moteur NoSQL, telles que la base de données Azure Cosmos, MongoDB, Cassandra, RavenDB, CouchDB ou Tables de stockage Azure.

Toutefois, lorsque vous utilisez une base de données NoSQL, en particulier un orienté document de base de données comme base de données Azure Cosmos, CouchDB ou RavenDB, la manière dont vous concevez votre modèle avec les agrégats DDD est partiellement similaire à la façon dont vous pouvez le faire dans EF Core, en ce qui concerne l’identification des racines d’agrégat, les classes d’entité enfant et les classes d’objet de valeur. Toutefois, pour finir, la sélection de la base de données aura un impact sur votre conception.

Lorsque vous utilisez une base de données orienté document, vous implémentez un agrégat comme un document unique, sérialisé dans JSON ou un autre format. Toutefois, l’utilisation de la base de données est transparente à partir d’un domaine modèle code point de vue. Lorsque vous utilisez une base de données NoSQL, toujours utiliser les classes d’entité et classes racines d’agrégation, mais avec plus de souplesse que lors de l’utilisation d’EF Core, car la persistance n’est pas relationnelle.

La différence réside dans la persistance de ce modèle. Si vous avez implémenté votre modèle de domaine basé sur les classes d’entité POCO, indépendant de la persistance de l’infrastructure, il peut se présenter comme vous pouvez vous déplacer vers une infrastructure de persistance différent, même à partir de relationnelle à NoSQL. Toutefois, qui ne doit pas être votre objectif. Il existe toujours des contraintes dans les bases de données vous fera, donc vous ne pourrez pas utiliser le même modèle pour relationnelles ou des bases de données NoSQL. Modification des modèles de persistance ne serait pas triviale, étant donné que les transactions et les opérations de persistance seront très différentes.

Par exemple, dans une base de données orienté document, il est OK pour une racine d’agrégat à avoir plusieurs propriétés de collection enfant. Dans une base de données relationnelle, interrogation de plusieurs propriétés de collection enfant est énorme, étant donné que vous obtenez une instruction SQL UNION ALL FE. Ayant le même modèle de domaine pour les bases de données relationnelles ou des bases de données NoSQL n’est pas simple, et pas essayez-le. Vous devez concevoir votre modèle de comprendre comment les données va être utilisée dans chaque base de données particulière.

Un avantage lorsque vous utilisez des bases de données NoSQL est que les entités sont plus dénormalisées, donc vous ne définissez pas un mappage de table. Votre modèle de domaine peut être plus flexible que lorsque vous utilisez une base de données relationnelle.

Lorsque vous concevez votre modèle de domaine basé sur des agrégats, déplacement vers NoSQL et bases de données orienté document peuvent être encore plus simple que l’utilisation d’une base de données relationnelle, étant donné que les agrégats que vous créez sont semblables aux sérialisée des documents dans une base de données orienté document. Puis vous pouvez inclure dans ces « conteneurs » toutes les informations que vous pouvez avoir besoin pour ce regroupement.

Par exemple, le code JSON suivant est un exemple d’implémentation d’un agrégat de commande lors de l’utilisation d’une base de données orienté document. Il est similaire à la commande d’agrégation, que nous avons implémenté dans l’exemple eShopOnContainers, mais sans utiliser EF sous-jacents.

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

Lorsque vous utilisez un C\# modèle pour implémenter l’agrégat utilisable par quelque chose comme Azure Cosmos DB SDK, l’agrégat est semblable à la C\# utilisés avec EF de base des classes POCO. La différence réside dans la façon de les utiliser dans les couches application et d’infrastructure, comme dans le code suivant :

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH DOCUMENTDB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).
// This can be saved as JSON as is without converting into rows/columns.
Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);
OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

OrderItem orderItem2 = new OrderItem
{
    Id = 20170012,
    ProductId = "123457",
    ProductName = ".NET Mug",
    UnitPrice = 15,
    Units = 1,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
orderAggregate.AddOrderItem(orderItem2);

// *** End of Domain Model Code ***
//...
// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, order);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

Vous pouvez voir que la façon de travailler avec votre modèle de domaine peut être semblable à la façon dont vous utilisez dans votre couche de modèle de domaine lors de l’infrastructure est EF. Vous utilisez toujours les mêmes méthodes d’agrégation racine pour garantir la cohérence, les invariants et les validations au sein de l’agrégat.

Toutefois, lorsque vous conserver votre modèle dans la base de données NoSQL, le code et modification d’API considérablement par rapport au code EF principal ou tout autre code lié bases de données relationnelles.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Modélisation des données dans DocumentDB**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)

-   **Vaughn Vernon. Le magasin d’agrégat pilotée par domaine conception idéal ? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **Une indépendance de la persistance magasin d’événements pour .NET.** Référentiel GitHub.
    [*https://github.com/NEventStore/NEventStore*](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
[Précédente] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [suivant] (microservice-application-layer-web-api-design.md)
