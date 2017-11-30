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
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="ccce8-104">À l’aide de bases de données NoSQL comme une infrastructure de persistance</span><span class="sxs-lookup"><span data-stu-id="ccce8-104">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="ccce8-105">Lorsque vous utilisez des bases de données NoSQL pour votre couche de données d’infrastructure, vous n’utilisez généralement pas un ORM comme Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="ccce8-105">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="ccce8-106">Au lieu de cela, vous utilisez l’API fournie par le moteur NoSQL, telles que la base de données Azure Cosmos, MongoDB, Cassandra, RavenDB, CouchDB ou Tables de stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="ccce8-106">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="ccce8-107">Toutefois, lorsque vous utilisez une base de données NoSQL, en particulier un orienté document de base de données comme base de données Azure Cosmos, CouchDB ou RavenDB, la manière dont vous concevez votre modèle avec les agrégats DDD est partiellement similaire à la façon dont vous pouvez le faire dans EF Core, en ce qui concerne l’identification des racines d’agrégat, les classes d’entité enfant et les classes d’objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="ccce8-107">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="ccce8-108">Toutefois, pour finir, la sélection de la base de données aura un impact sur votre conception.</span><span class="sxs-lookup"><span data-stu-id="ccce8-108">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="ccce8-109">Lorsque vous utilisez une base de données orienté document, vous implémentez un agrégat comme un document unique, sérialisé dans JSON ou un autre format.</span><span class="sxs-lookup"><span data-stu-id="ccce8-109">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="ccce8-110">Toutefois, l’utilisation de la base de données est transparente à partir d’un domaine modèle code point de vue.</span><span class="sxs-lookup"><span data-stu-id="ccce8-110">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="ccce8-111">Lorsque vous utilisez une base de données NoSQL, toujours utiliser les classes d’entité et classes racines d’agrégation, mais avec plus de souplesse que lors de l’utilisation d’EF Core, car la persistance n’est pas relationnelle.</span><span class="sxs-lookup"><span data-stu-id="ccce8-111">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="ccce8-112">La différence réside dans la persistance de ce modèle.</span><span class="sxs-lookup"><span data-stu-id="ccce8-112">The difference is in how you persist that model.</span></span> <span data-ttu-id="ccce8-113">Si vous avez implémenté votre modèle de domaine basé sur les classes d’entité POCO, indépendant de la persistance de l’infrastructure, il peut se présenter comme vous pouvez vous déplacer vers une infrastructure de persistance différent, même à partir de relationnelle à NoSQL.</span><span class="sxs-lookup"><span data-stu-id="ccce8-113">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="ccce8-114">Toutefois, qui ne doit pas être votre objectif.</span><span class="sxs-lookup"><span data-stu-id="ccce8-114">However, that should not be your goal.</span></span> <span data-ttu-id="ccce8-115">Il existe toujours des contraintes dans les bases de données vous fera, donc vous ne pourrez pas utiliser le même modèle pour relationnelles ou des bases de données NoSQL.</span><span class="sxs-lookup"><span data-stu-id="ccce8-115">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="ccce8-116">Modification des modèles de persistance ne serait pas triviale, étant donné que les transactions et les opérations de persistance seront très différentes.</span><span class="sxs-lookup"><span data-stu-id="ccce8-116">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="ccce8-117">Par exemple, dans une base de données orienté document, il est OK pour une racine d’agrégat à avoir plusieurs propriétés de collection enfant.</span><span class="sxs-lookup"><span data-stu-id="ccce8-117">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="ccce8-118">Dans une base de données relationnelle, interrogation de plusieurs propriétés de collection enfant est énorme, étant donné que vous obtenez une instruction SQL UNION ALL FE.</span><span class="sxs-lookup"><span data-stu-id="ccce8-118">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="ccce8-119">Ayant le même modèle de domaine pour les bases de données relationnelles ou des bases de données NoSQL n’est pas simple, et pas essayez-le.</span><span class="sxs-lookup"><span data-stu-id="ccce8-119">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="ccce8-120">Vous devez concevoir votre modèle de comprendre comment les données va être utilisée dans chaque base de données particulière.</span><span class="sxs-lookup"><span data-stu-id="ccce8-120">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="ccce8-121">Un avantage lorsque vous utilisez des bases de données NoSQL est que les entités sont plus dénormalisées, donc vous ne définissez pas un mappage de table.</span><span class="sxs-lookup"><span data-stu-id="ccce8-121">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="ccce8-122">Votre modèle de domaine peut être plus flexible que lorsque vous utilisez une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="ccce8-122">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="ccce8-123">Lorsque vous concevez votre modèle de domaine basé sur des agrégats, déplacement vers NoSQL et bases de données orienté document peuvent être encore plus simple que l’utilisation d’une base de données relationnelle, étant donné que les agrégats que vous créez sont semblables aux sérialisée des documents dans une base de données orienté document.</span><span class="sxs-lookup"><span data-stu-id="ccce8-123">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="ccce8-124">Puis vous pouvez inclure dans ces « conteneurs » toutes les informations que vous pouvez avoir besoin pour ce regroupement.</span><span class="sxs-lookup"><span data-stu-id="ccce8-124">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="ccce8-125">Par exemple, le code JSON suivant est un exemple d’implémentation d’un agrégat de commande lors de l’utilisation d’une base de données orienté document.</span><span class="sxs-lookup"><span data-stu-id="ccce8-125">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="ccce8-126">Il est similaire à la commande d’agrégation, que nous avons implémenté dans l’exemple eShopOnContainers, mais sans utiliser EF sous-jacents.</span><span class="sxs-lookup"><span data-stu-id="ccce8-126">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

<span data-ttu-id="ccce8-127">Lorsque vous utilisez un C\# modèle pour implémenter l’agrégat utilisable par quelque chose comme Azure Cosmos DB SDK, l’agrégat est semblable à la C\# utilisés avec EF de base des classes POCO.</span><span class="sxs-lookup"><span data-stu-id="ccce8-127">When you use a C\# model to implement the aggregate to be used by something like the Azure Cosmos DB SDK, the aggregate is similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="ccce8-128">La différence réside dans la façon de les utiliser dans les couches application et d’infrastructure, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ccce8-128">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="ccce8-129">Vous pouvez voir que la façon de travailler avec votre modèle de domaine peut être semblable à la façon dont vous utilisez dans votre couche de modèle de domaine lors de l’infrastructure est EF.</span><span class="sxs-lookup"><span data-stu-id="ccce8-129">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="ccce8-130">Vous utilisez toujours les mêmes méthodes d’agrégation racine pour garantir la cohérence, les invariants et les validations au sein de l’agrégat.</span><span class="sxs-lookup"><span data-stu-id="ccce8-130">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="ccce8-131">Toutefois, lorsque vous conserver votre modèle dans la base de données NoSQL, le code et modification d’API considérablement par rapport au code EF principal ou tout autre code lié bases de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="ccce8-131">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="ccce8-132">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="ccce8-132">Additional resources</span></span>

-   <span data-ttu-id="ccce8-133">**Modélisation des données dans DocumentDB**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span><span class="sxs-lookup"><span data-stu-id="ccce8-133">**Modeling data in DocumentDB**
[*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span></span>

-   <span data-ttu-id="ccce8-134">**Vaughn Vernon. Le magasin d’agrégat pilotée par domaine conception idéal ? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="ccce8-134">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="ccce8-135">**Une indépendance de la persistance magasin d’événements pour .NET.**</span><span class="sxs-lookup"><span data-stu-id="ccce8-135">**A persistence agnostic Event Store for .NET.**</span></span> <span data-ttu-id="ccce8-136">Référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="ccce8-136">GitHub repo.</span></span>
    [<span data-ttu-id="ccce8-137">*https://github.com/NEventStore/NEventStore*</span><span class="sxs-lookup"><span data-stu-id="ccce8-137">*https://github.com/NEventStore/NEventStore*</span></span>](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
<span data-ttu-id="ccce8-138">[Précédente] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [suivant] (microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="ccce8-138">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span></span>
