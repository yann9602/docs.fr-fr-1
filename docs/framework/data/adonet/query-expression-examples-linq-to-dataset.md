---
title: "Exemples d'expression de requête (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1967575aa7a287064d6da54d929ce095e89ee24f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="5c319-102">Exemples d'expression de requête (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="5c319-102">Query Expression Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="5c319-103">Cette section fournit des exemples de programmation [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dans une syntaxe d'expression de requête qui utilise des opérateurs de requête standard.</span><span class="sxs-lookup"><span data-stu-id="5c319-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="5c319-104">Le <xref:System.Data.DataSet> utilisé dans ces exemples est rempli à l’aide de la `FillDataSet` (méthode), qui est spécifié dans [chargement des données dans un groupe de données](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5c319-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="5c319-105">Pour plus d’informations, consultez [vue d’ensemble des opérateurs de requête Standard](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="5c319-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c319-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5c319-106">In This Section</span></span>  
 [<span data-ttu-id="5c319-107">Projection</span><span class="sxs-lookup"><span data-stu-id="5c319-107">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="5c319-108">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.Select%2A> et <xref:System.Linq.Enumerable.SelectMany%2A> pour interroger un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5c319-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="5c319-109">Restriction</span><span class="sxs-lookup"><span data-stu-id="5c319-109">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="5c319-110">Les exemples de cette rubrique montrent comment utiliser la méthode <xref:System.Linq.Enumerable.Where%2A> pour interroger un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5c319-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="5c319-111">Le partitionnement</span><span class="sxs-lookup"><span data-stu-id="5c319-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="5c319-112">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Take%2A> pour interroger un <xref:System.Data.DataSet> et partitionner les résultats.</span><span class="sxs-lookup"><span data-stu-id="5c319-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="5c319-113">Classement</span><span class="sxs-lookup"><span data-stu-id="5c319-113">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="5c319-114">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A> et <xref:System.Linq.Enumerable.ThenByDescending%2A> pour interroger un <xref:System.Data.DataSet> et classer les résultats.</span><span class="sxs-lookup"><span data-stu-id="5c319-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="5c319-115">Opérateurs d’élément</span><span class="sxs-lookup"><span data-stu-id="5c319-115">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="5c319-116">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.First%2A> et <xref:System.Linq.Enumerable.ElementAt%2A> pour obtenir des éléments <xref:System.Data.DataRow> à partir d'un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5c319-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="5c319-117">Opérateurs d’agrégation</span><span class="sxs-lookup"><span data-stu-id="5c319-117">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="5c319-118">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A> et <xref:System.Linq.Enumerable.Sum%2A> pour interroger un <xref:System.Data.DataSet> et agréger les données.</span><span class="sxs-lookup"><span data-stu-id="5c319-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="5c319-119">Opérateurs de jointure</span><span class="sxs-lookup"><span data-stu-id="5c319-119">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="5c319-120">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.GroupJoin%2A> et <xref:System.Linq.Enumerable.Join%2A> pour interroger un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5c319-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c319-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c319-121">See Also</span></span>  
 [<span data-ttu-id="5c319-122">Exemples de requête fondée sur une méthode</span><span class="sxs-lookup"><span data-stu-id="5c319-122">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 [<span data-ttu-id="5c319-123">Exemples d’opérateurs spécifiques aux DataSets</span><span class="sxs-lookup"><span data-stu-id="5c319-123">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [<span data-ttu-id="5c319-124">LINQ to DataSet Examples</span><span class="sxs-lookup"><span data-stu-id="5c319-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
