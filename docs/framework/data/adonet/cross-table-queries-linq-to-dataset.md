---
title: "Requêtes d'analyse croisée (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0b829840257dc2b3b4bbf0b8c3a294a77060e2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cross-table-queries-linq-to-dataset"></a><span data-ttu-id="7df8c-102">Requêtes d'analyse croisée (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7df8c-102">Cross-Table Queries (LINQ to DataSet)</span></span>
<span data-ttu-id="7df8c-103">Outre l'interrogation d'une table unique, vous pouvez également exécuter des requêtes à tables croisées dans [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7df8c-103">In addition to querying a single table, you can also perform cross-table queries in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="7df8c-104">Cela en utilisant un *jointure*.</span><span class="sxs-lookup"><span data-stu-id="7df8c-104">This is done by using a *join*.</span></span> <span data-ttu-id="7df8c-105">Une jointure est l'association d'objets d'une source de données avec des objets qui partagent un attribut commun dans une autre source de données, comme un produit ou un ID de contact.</span><span class="sxs-lookup"><span data-stu-id="7df8c-105">A join is the association of objects in one data source with objects that share a common attribute in another data source, such as a product or contact ID.</span></span> <span data-ttu-id="7df8c-106">Dans la programmation orientée objets, les relations entre les objets sont relativement faciles à explorer car chaque objet possède un membre faisant référence à un autre objet.</span><span class="sxs-lookup"><span data-stu-id="7df8c-106">In object-oriented programming, relationships between objects are relatively easy to navigate because each object has a member that references another object.</span></span> <span data-ttu-id="7df8c-107">Dans les tables de base de données externe, toutefois, l'exploration des relations n'est pas aussi simple.</span><span class="sxs-lookup"><span data-stu-id="7df8c-107">In external database tables, however, navigating relationships is not as straightforward.</span></span> <span data-ttu-id="7df8c-108">Les tables de base de données ne contiennent pas de relations intégrées.</span><span class="sxs-lookup"><span data-stu-id="7df8c-108">Database tables do not contain built-in relationships.</span></span> <span data-ttu-id="7df8c-109">Dans ces cas particuliers, l'opération de jointure peut servir à faire correspondre des éléments de chaque source.</span><span class="sxs-lookup"><span data-stu-id="7df8c-109">In these cases, the join operation can be used to match elements from each source.</span></span> <span data-ttu-id="7df8c-110">Par exemple, avec deux tables qui contiennent des informations sur les produits et des informations sur les ventes, vous pourriez utiliser une opération de jointure pour faire correspondre les informations sur les ventes et les produits pour la même commande.</span><span class="sxs-lookup"><span data-stu-id="7df8c-110">For example, given two tables that contain product information and sales information, you could use a join operation to match sales information and products for the same sales order.</span></span>  
  
 <span data-ttu-id="7df8c-111">L'infrastructure [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] fournit deux opérateurs de jointure, <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="7df8c-111">The [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] framework provides two join operators, <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="7df8c-112">Ces opérateurs effectuent *équijointures*: autrement dit, les jointures qui correspondent aux données de deux sources uniquement lorsque leurs clés sont égales.</span><span class="sxs-lookup"><span data-stu-id="7df8c-112">These operators perform *equi-joins*: that is, joins that match two data sources only when their keys are equal.</span></span> <span data-ttu-id="7df8c-113">(Par contraste, [!INCLUDE[tsql](../../../../includes/tsql-md.md)] prend en charge des opérateurs de jointure autres que `equals`, comme l'opérateur `less than`.)</span><span class="sxs-lookup"><span data-stu-id="7df8c-113">(By contrast, [!INCLUDE[tsql](../../../../includes/tsql-md.md)] supports join operators other than `equals`, such as the `less than` operator.)</span></span>  
  
 <span data-ttu-id="7df8c-114">En termes de base de données relationnelle, <xref:System.Linq.Enumerable.Join%2A> implémente une jointure interne.</span><span class="sxs-lookup"><span data-stu-id="7df8c-114">In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join.</span></span> <span data-ttu-id="7df8c-115">Une jointure interne est un type de jointure dans lequel seuls les objets qui ont une correspondance dans le data set opposé sont retournés.</span><span class="sxs-lookup"><span data-stu-id="7df8c-115">An inner join is a type of join in which only those objects that have a match in the opposite data set are returned.</span></span>  
  
 <span data-ttu-id="7df8c-116">Le <xref:System.Linq.Enumerable.GroupJoin%2A> opérateurs n’ont aucun équivalent direct en termes de base de données relationnelle ; elles implémentent un sur-ensemble de jointures internes et de jointures externes gauches.</span><span class="sxs-lookup"><span data-stu-id="7df8c-116">The <xref:System.Linq.Enumerable.GroupJoin%2A> operators have no direct equivalent in relational database terms; they implement a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="7df8c-117">Une jointure externe gauche est une jointure qui retourne chaque élément de la première collection (gauche), même si elle n’a pas d’éléments corrélés dans la seconde collection.</span><span class="sxs-lookup"><span data-stu-id="7df8c-117">A left outer join is a join that returns each element of the first (left) collection, even if it has no correlated elements in the second collection.</span></span>  
  
 <span data-ttu-id="7df8c-118">Pour plus d’informations sur les jointures, consultez [les opérations de jointures](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span><span class="sxs-lookup"><span data-stu-id="7df8c-118">For more information about joins, see [Join Operations](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7df8c-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="7df8c-119">Example</span></span>  
 <span data-ttu-id="7df8c-120">L'exemple suivant effectue une jointure traditionnelle des tables `SalesOrderHeader` et `SalesOrderDetail` de l'exemple de base de données AdventureWorks pour obtenir les commandes en ligne du mois d'août.</span><span class="sxs-lookup"><span data-stu-id="7df8c-120">The following example performs a traditional join of the `SalesOrderHeader` and `SalesOrderDetail` tables from the AdventureWorks sample database to obtain online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="7df8c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7df8c-121">See Also</span></span>  
 [<span data-ttu-id="7df8c-122">Interrogation de DataSets</span><span class="sxs-lookup"><span data-stu-id="7df8c-122">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="7df8c-123">Requêtes d’analyse unique</span><span class="sxs-lookup"><span data-stu-id="7df8c-123">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="7df8c-124">Interrogation de DataSets typés</span><span class="sxs-lookup"><span data-stu-id="7df8c-124">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [<span data-ttu-id="7df8c-125">Opérations de jointure</span><span class="sxs-lookup"><span data-stu-id="7df8c-125">Join Operations</span></span>](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [<span data-ttu-id="7df8c-126">LINQ to DataSet Examples</span><span class="sxs-lookup"><span data-stu-id="7df8c-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
