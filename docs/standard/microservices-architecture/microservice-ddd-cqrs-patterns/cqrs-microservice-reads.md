---
title: "Implémentation des lectures/requêtes dans un microservice CQRS"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation des lectures/requêtes dans un microservice CQRS"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e017aaaa701d8033110be8d6244d3e1120fc4fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="96ba5-104">Implémentation des lectures/requêtes dans un microservice CQRS</span><span class="sxs-lookup"><span data-stu-id="96ba5-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="96ba5-105">Pour les lectures/requêtes, le tri microservice à partir de l’application de référence eShopOnContainers implémente les requêtes indépendamment de la zone transactionnelle et le modèle DDD.</span><span class="sxs-lookup"><span data-stu-id="96ba5-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="96ba5-106">Ceci permet principalement du fait que le nombre de demandes pour les requêtes et pour les transactions est considérablement différentes.</span><span class="sxs-lookup"><span data-stu-id="96ba5-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="96ba5-107">Écritures exécutent des transactions qui doivent être conformes à la logique de domaine.</span><span class="sxs-lookup"><span data-stu-id="96ba5-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="96ba5-108">En revanche, les requêtes, sont idempotents et peuvent être séparés des règles de domaine.</span><span class="sxs-lookup"><span data-stu-id="96ba5-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="96ba5-109">L’approche est simple, comme indiqué dans la Figure 9-3.</span><span class="sxs-lookup"><span data-stu-id="96ba5-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="96ba5-110">L’interface API est implémentée par les contrôleurs de l’API Web à l’aide de n’importe quelle infrastructure (par exemple, un micro ORM comme Dapper) et en retournant les ViewModel dynamique selon les besoins des applications d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="96ba5-110">The API interface is implemented by the Web API controllers using any infrastructure (such as a micro ORM like Dapper) and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="96ba5-111">**Figure 9-3**.</span><span class="sxs-lookup"><span data-stu-id="96ba5-111">**Figure 9-3**.</span></span> <span data-ttu-id="96ba5-112">L’approche la plus simple pour les requêtes dans un microservice CQRS</span><span class="sxs-lookup"><span data-stu-id="96ba5-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="96ba5-113">Il s’agit de l’approche la plus simple possible pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="96ba5-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="96ba5-114">Les définitions de requête interroger la base de données et retournent un ViewModel dynamique généré à la volée pour chaque requête.</span><span class="sxs-lookup"><span data-stu-id="96ba5-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="96ba5-115">Étant donné que les requêtes sont idempotents, ils ne changera pas les données, quel que soit le nombre de fois où vous exécutez une requête.</span><span class="sxs-lookup"><span data-stu-id="96ba5-115">Since the queries are idempotent, they will not change the data no matter how many times you run a query.</span></span> <span data-ttu-id="96ba5-116">Par conséquent, vous n’avez pas besoin être restreints par n’importe quel modèle DDD utilisé côté transactionnels, telles que les agrégats et les autres modèles, et c’est pourquoi les requêtes sont séparés à partir de la zone transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="96ba5-116">Therefore, you do not need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="96ba5-117">Vous simplement interrogez la base de données pour les données dont a besoin de l’interface utilisateur et renvoyer un ViewModel dynamique qui ne doive pas être statiquement en tout lieu (aucune classe pour les ViewModel) défini à l’exception dans les instructions SQL elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="96ba5-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="96ba5-118">Dans la mesure où il s’agit d’une approche simple, le code requis pour le côté de requêtes (tel que le code à l’aide d’un micro ORM comme [Dapper](https://github.com/StackExchange/Dapper)) peuvent être implémentées [dans le même projet d’API Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="96ba5-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="96ba5-119">Figure 9-4 illustre ce point.</span><span class="sxs-lookup"><span data-stu-id="96ba5-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="96ba5-120">Les requêtes sont définies dans le **Ordering.API** projet microservice au sein de la solution eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="96ba5-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="96ba5-121">**Figure 9-4**.</span><span class="sxs-lookup"><span data-stu-id="96ba5-121">**Figure 9-4**.</span></span> <span data-ttu-id="96ba5-122">Requêtes dans le classement microservice dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="96ba5-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="96ba5-123">À l’aide de ViewModel apportées en particulier pour les applications clientes, indépendantes de contraintes de modèle de domaine</span><span class="sxs-lookup"><span data-stu-id="96ba5-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="96ba5-124">Étant donné que les requêtes sont exécutées pour obtenir les données requises par les applications clientes, le type retourné est plus précisément possible pour les clients basés sur les données retournées par les requêtes.</span><span class="sxs-lookup"><span data-stu-id="96ba5-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="96ba5-125">Ces modèles, ou des objets de transfert de données (DTO), sont appelés ViewModel.</span><span class="sxs-lookup"><span data-stu-id="96ba5-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="96ba5-126">Les données retournées (ViewModel) peuvent être le résultat de la jointure de données à partir de plusieurs entités ou tables dans la base de données, ou même à travers plusieurs agrégats définis dans le modèle de domaine pour la zone transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="96ba5-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="96ba5-127">Dans ce cas, étant donné que vous créez des requêtes indépendantes du modèle de domaine, les limites d’agrégats et les contraintes sont ignorées complètement et vous êtes libre d’interroger les tables et les colonnes que vous devrez peut-être.</span><span class="sxs-lookup"><span data-stu-id="96ba5-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you are free to query any table and column you might need.</span></span> <span data-ttu-id="96ba5-128">Cette approche offre une grande souplesse et productivité pour les développeurs de créer ou mettre à jour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="96ba5-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="96ba5-129">Les ViewModel peuvent être définis dans les classes de types static.</span><span class="sxs-lookup"><span data-stu-id="96ba5-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="96ba5-130">Ou ils peuvent être créés de manière dynamique sur les requêtes effectuées (tel qu’il est implémenté dans l’ordre de tri microservice), qui est très souple pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="96ba5-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="96ba5-131">À l’aide de Dapper en tant qu’un micro ORM pour effectuer des requêtes</span><span class="sxs-lookup"><span data-stu-id="96ba5-131">Using Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="96ba5-132">Vous pouvez utiliser tout micro ORM, Entity Framework Core ou même brut ADO.NET pour l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="96ba5-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="96ba5-133">Dans l’exemple d’application, nous avons sélectionné Dapper pour le tri microservice dans eShopOnContainers un bon exemple d’un ORM micro populaires.</span><span class="sxs-lookup"><span data-stu-id="96ba5-133">In the sample application, we selected Dapper for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="96ba5-134">Vous pouvez exécuter des requêtes SQL simples dotées de hautes performances, car il s’agit d’une infrastructure très légère.</span><span class="sxs-lookup"><span data-stu-id="96ba5-134">It can run plain SQL queries with great performance, because it is a very light framework.</span></span> <span data-ttu-id="96ba5-135">À l’aide de Dapper, vous pouvez écrire une requête SQL qui peut accéder à et joindre plusieurs tables.</span><span class="sxs-lookup"><span data-stu-id="96ba5-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="96ba5-136">Dapper est un projet open source (original créé par Sam Saffron) et fait partie des blocs de construction utilisés dans [débordement de pile](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="96ba5-136">Dapper is an open source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="96ba5-137">Pour utiliser Dapper, il vous suffit de l’installer via la [package NuGet Dapper](https://www.nuget.org/packages/Dapper), comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="96ba5-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure.</span></span>

![](./media/image5.png)

<span data-ttu-id="96ba5-138">Vous devez également ajouter un en utilisant la déclaration de sorte que votre code a accès aux méthodes d’extension Dapper.</span><span class="sxs-lookup"><span data-stu-id="96ba5-138">You will also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="96ba5-139">Lorsque vous utilisez Dapper dans votre code, vous utilisez directement la classe SqlClient disponible dans l’espace de noms System.Data.SqlClient.</span><span class="sxs-lookup"><span data-stu-id="96ba5-139">When you use Dapper in your code, you directly use the SqlClient class available in the System.Data.SqlClient namespace.</span></span> <span data-ttu-id="96ba5-140">Grâce à la méthode QueryAsync et d’autres méthodes d’extension qui étendent la classe SqlClient, vous pouvez simplement exécuter des requêtes de manière simple et performant.</span><span class="sxs-lookup"><span data-stu-id="96ba5-140">Through the QueryAsync method and other extension methods which extend the SqlClient class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-and-static-viewmodels"></a><span data-ttu-id="96ba5-141">ViewModel dynamique et statique</span><span class="sxs-lookup"><span data-stu-id="96ba5-141">Dynamic and static ViewModels</span></span>

<span data-ttu-id="96ba5-142">Comme indiqué dans le code suivant à partir de la commande microservice, la plupart des ViewModel retournées par les requêtes est implémentée en tant que *dynamique*.</span><span class="sxs-lookup"><span data-stu-id="96ba5-142">As shown in the following code from the ordering microservice, most of the ViewModels returned by the queries are implemented as *dynamic*.</span></span> <span data-ttu-id="96ba5-143">Cela signifie que le sous-ensemble des attributs à retourner est basé sur la requête elle-même.</span><span class="sxs-lookup"><span data-stu-id="96ba5-143">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="96ba5-144">Si vous ajoutez une nouvelle colonne à la requête ou d’une jointure, ces données sont ajoutées dynamiquement au ViewModel retourné.</span><span class="sxs-lookup"><span data-stu-id="96ba5-144">If you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span> <span data-ttu-id="96ba5-145">Cette approche réduit le besoin de modifier des requêtes en réponse aux mises à jour du modèle de données sous-jacent, qui effectue cette approche de conception plus flexible et à tolérance de panne des futures modifications.</span><span class="sxs-lookup"><span data-stu-id="96ba5-145">This approach reduces the need to modify queries in response to updates to the underlying data model, making this design approach more flexible and tolerant of future changes.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
@"SELECT o.[Id] as ordernumber,
o.[OrderDate] as [date],os.[Name] as [status],
SUM(oi.units*oi.unitprice) as total
FROM [ordering].[Orders] o
LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
  }
}
```

<span data-ttu-id="96ba5-146">Le point important est qu’en utilisant un type dynamique, la collection retournée de données sera dynamiquement assemblée comme ViewModel.</span><span class="sxs-lookup"><span data-stu-id="96ba5-146">The important point is that by using a dynamic type, the returned collection of data will be dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="96ba5-147">Pour la plupart des requêtes, vous n’avez pas besoin de prédéfinir une classe DTO ou ViewModel, ce qui rend les coder de manière simple et productive.</span><span class="sxs-lookup"><span data-stu-id="96ba5-147">For most queries, you do not need to predefine a DTO or ViewModel class, which makes coding them straightforward and productive.</span></span> <span data-ttu-id="96ba5-148">Toutefois, vous pouvez prédéfinir ViewModel (comme DTO prédéfinis) si vous souhaitez avoir ViewModel avec une définition plus restreinte comme des contrats.</span><span class="sxs-lookup"><span data-stu-id="96ba5-148">However, you can predefine ViewModels (like predefined DTOs) if you want to have ViewModels with a more restricted definition as contracts.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="96ba5-149">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="96ba5-149">Additional resources</span></span>

-   <span data-ttu-id="96ba5-150">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="96ba5-150">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="96ba5-151">**Julie Lerman. Points de données - Dapper, Entity Framework et les applications hybrides (article MSDN champ)**</span><span class="sxs-lookup"><span data-stu-id="96ba5-151">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="96ba5-152">*https://msdn.Microsoft.com/en-us/Magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="96ba5-152">*https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="96ba5-153">[Précédente] (eshoponcontainers-cqrs-ddd-microservice.md) [suivant] (ddd-orientée-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="96ba5-153">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
