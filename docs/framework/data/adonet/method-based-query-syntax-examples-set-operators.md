---
title: "Exemples de syntaxe de requête fondée sur une méthode : opérateurs de jeu (LINQ to DataSet)"
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
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d2e33ee55023db7a84109cd3c94a4c8b3b49e1c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="df6a1-102">Exemples de syntaxe de requête fondée sur une méthode : opérateurs de jeu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="df6a1-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="df6a1-103">Les exemples de cette rubrique montrent comment utiliser le <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, et <xref:System.Linq.Enumerable.Union%2A> opérateurs pour effectuer des opérations de comparaison de valeur basée sur des ensembles de lignes de données.[ Chargement des données dans un groupe de données](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) consultez [comparaison de DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) pour plus d’informations sur <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="df6a1-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) See [Comparing DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="df6a1-104">Le `FillDataSet` méthode utilisé dans ces exemples est spécifiée dans [chargement des données dans un groupe de données](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="df6a1-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="df6a1-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="df6a1-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="df6a1-106">Les exemples de cette rubrique utilisent les éléments suivants `using` / `Imports` instructions :</span><span class="sxs-lookup"><span data-stu-id="df6a1-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="df6a1-107">Pour plus d’informations, consultez [Comment : créer une LINQ to DataSet Project dans Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="df6a1-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="df6a1-108">distinct</span><span class="sxs-lookup"><span data-stu-id="df6a1-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="df6a1-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="df6a1-109">Example</span></span>  
 <span data-ttu-id="df6a1-110">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Distinct%2A> pour supprimer des éléments en double dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="df6a1-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="df6a1-111">Except</span><span class="sxs-lookup"><span data-stu-id="df6a1-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="df6a1-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="df6a1-112">Example</span></span>  
 <span data-ttu-id="df6a1-113">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Except%2A> pour retourner les contacts qui apparaissent dans la première table, mais pas dans la seconde.</span><span class="sxs-lookup"><span data-stu-id="df6a1-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="df6a1-114">Intersection</span><span class="sxs-lookup"><span data-stu-id="df6a1-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="df6a1-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="df6a1-115">Example</span></span>  
 <span data-ttu-id="df6a1-116">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Intersect%2A> pour retourner les contacts qui apparaissent dans les deux tables.</span><span class="sxs-lookup"><span data-stu-id="df6a1-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="df6a1-117">Union</span><span class="sxs-lookup"><span data-stu-id="df6a1-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="df6a1-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="df6a1-118">Example</span></span>  
 <span data-ttu-id="df6a1-119">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Union%2A> pour retourner des contacts uniques dans l'une ou l'autre des tables.</span><span class="sxs-lookup"><span data-stu-id="df6a1-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="df6a1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df6a1-120">See Also</span></span>  
 [<span data-ttu-id="df6a1-121">Chargement des données dans un jeu de données</span><span class="sxs-lookup"><span data-stu-id="df6a1-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="df6a1-122">LINQ to DataSet Examples</span><span class="sxs-lookup"><span data-stu-id="df6a1-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="df6a1-123">Vue d’ensemble des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="df6a1-123">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
