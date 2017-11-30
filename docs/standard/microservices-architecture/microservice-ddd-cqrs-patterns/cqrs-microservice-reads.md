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
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>Implémentation des lectures/requêtes dans un microservice CQRS

Pour les lectures/requêtes, le tri microservice à partir de l’application de référence eShopOnContainers implémente les requêtes indépendamment de la zone transactionnelle et le modèle DDD. Ceci permet principalement du fait que le nombre de demandes pour les requêtes et pour les transactions est considérablement différentes. Écritures exécutent des transactions qui doivent être conformes à la logique de domaine. En revanche, les requêtes, sont idempotents et peuvent être séparés des règles de domaine.

L’approche est simple, comme indiqué dans la Figure 9-3. L’interface API est implémentée par les contrôleurs de l’API Web à l’aide de n’importe quelle infrastructure (par exemple, un micro ORM comme Dapper) et en retournant les ViewModel dynamique selon les besoins des applications d’interface utilisateur.

![](./media/image3.png)

**Figure 9-3**. L’approche la plus simple pour les requêtes dans un microservice CQRS

Il s’agit de l’approche la plus simple possible pour les requêtes. Les définitions de requête interroger la base de données et retournent un ViewModel dynamique généré à la volée pour chaque requête. Étant donné que les requêtes sont idempotents, ils ne changera pas les données, quel que soit le nombre de fois où vous exécutez une requête. Par conséquent, vous n’avez pas besoin être restreints par n’importe quel modèle DDD utilisé côté transactionnels, telles que les agrégats et les autres modèles, et c’est pourquoi les requêtes sont séparés à partir de la zone transactionnelle. Vous simplement interrogez la base de données pour les données dont a besoin de l’interface utilisateur et renvoyer un ViewModel dynamique qui ne doive pas être statiquement en tout lieu (aucune classe pour les ViewModel) défini à l’exception dans les instructions SQL elles-mêmes.

Dans la mesure où il s’agit d’une approche simple, le code requis pour le côté de requêtes (tel que le code à l’aide d’un micro ORM comme [Dapper](https://github.com/StackExchange/Dapper)) peuvent être implémentées [dans le même projet d’API Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Figure 9-4 illustre ce point. Les requêtes sont définies dans le **Ordering.API** projet microservice au sein de la solution eShopOnContainers.

![](./media/image4.png)

**Figure 9-4**. Requêtes dans le classement microservice dans eShopOnContainers

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>À l’aide de ViewModel apportées en particulier pour les applications clientes, indépendantes de contraintes de modèle de domaine

Étant donné que les requêtes sont exécutées pour obtenir les données requises par les applications clientes, le type retourné est plus précisément possible pour les clients basés sur les données retournées par les requêtes. Ces modèles, ou des objets de transfert de données (DTO), sont appelés ViewModel.

Les données retournées (ViewModel) peuvent être le résultat de la jointure de données à partir de plusieurs entités ou tables dans la base de données, ou même à travers plusieurs agrégats définis dans le modèle de domaine pour la zone transactionnelle. Dans ce cas, étant donné que vous créez des requêtes indépendantes du modèle de domaine, les limites d’agrégats et les contraintes sont ignorées complètement et vous êtes libre d’interroger les tables et les colonnes que vous devrez peut-être. Cette approche offre une grande souplesse et productivité pour les développeurs de créer ou mettre à jour les requêtes.

Les ViewModel peuvent être définis dans les classes de types static. Ou ils peuvent être créés de manière dynamique sur les requêtes effectuées (tel qu’il est implémenté dans l’ordre de tri microservice), qui est très souple pour les développeurs.

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>À l’aide de Dapper en tant qu’un micro ORM pour effectuer des requêtes 

Vous pouvez utiliser tout micro ORM, Entity Framework Core ou même brut ADO.NET pour l’interrogation. Dans l’exemple d’application, nous avons sélectionné Dapper pour le tri microservice dans eShopOnContainers un bon exemple d’un ORM micro populaires. Vous pouvez exécuter des requêtes SQL simples dotées de hautes performances, car il s’agit d’une infrastructure très légère. À l’aide de Dapper, vous pouvez écrire une requête SQL qui peut accéder à et joindre plusieurs tables.

Dapper est un projet open source (original créé par Sam Saffron) et fait partie des blocs de construction utilisés dans [débordement de pile](https://stackoverflow.com/). Pour utiliser Dapper, il vous suffit de l’installer via la [package NuGet Dapper](https://www.nuget.org/packages/Dapper), comme indiqué dans l’illustration suivante.

![](./media/image5.png)

Vous devez également ajouter un en utilisant la déclaration de sorte que votre code a accès aux méthodes d’extension Dapper.

Lorsque vous utilisez Dapper dans votre code, vous utilisez directement la classe SqlClient disponible dans l’espace de noms System.Data.SqlClient. Grâce à la méthode QueryAsync et d’autres méthodes d’extension qui étendent la classe SqlClient, vous pouvez simplement exécuter des requêtes de manière simple et performant.

## <a name="dynamic-and-static-viewmodels"></a>ViewModel dynamique et statique

Comme indiqué dans le code suivant à partir de la commande microservice, la plupart des ViewModel retournées par les requêtes est implémentée en tant que *dynamique*. Cela signifie que le sous-ensemble des attributs à retourner est basé sur la requête elle-même. Si vous ajoutez une nouvelle colonne à la requête ou d’une jointure, ces données sont ajoutées dynamiquement au ViewModel retourné. Cette approche réduit le besoin de modifier des requêtes en réponse aux mises à jour du modèle de données sous-jacent, qui effectue cette approche de conception plus flexible et à tolérance de panne des futures modifications.

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

Le point important est qu’en utilisant un type dynamique, la collection retournée de données sera dynamiquement assemblée comme ViewModel.

Pour la plupart des requêtes, vous n’avez pas besoin de prédéfinir une classe DTO ou ViewModel, ce qui rend les coder de manière simple et productive. Toutefois, vous pouvez prédéfinir ViewModel (comme DTO prédéfinis) si vous souhaitez avoir ViewModel avec une définition plus restreinte comme des contrats.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman. Points de données - Dapper, Entity Framework et les applications hybrides (article MSDN champ)**

    *https://msdn.Microsoft.com/en-us/Magazine/mt703432.aspx*


>[!div class="step-by-step"]
[Précédente] (eshoponcontainers-cqrs-ddd-microservice.md) [suivant] (ddd-orientée-microservice.md)
