---
title: "Requêtes d'agrégation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d4aa6c0a9103bc4a906ecdfb51a55069e6b8b790
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="aggregate-queries"></a><span data-ttu-id="3024b-102">Requêtes d'agrégation</span><span class="sxs-lookup"><span data-stu-id="3024b-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="3024b-103"> prend en charge les opérateurs d'agrégation `Average`, `Count`, `Max`, `Min` et `Sum`.</span><span class="sxs-lookup"><span data-stu-id="3024b-103"> supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="3024b-104">Notez les caractéristiques suivantes des opérateurs d'agrégation dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="3024b-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="3024b-105">Les requêtes d'agrégation sont exécutées immédiatement.</span><span class="sxs-lookup"><span data-stu-id="3024b-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="3024b-106">Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="3024b-106">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="3024b-107">Les requêtes d’agrégation retournent généralement un nombre au lieu d’une collection.</span><span class="sxs-lookup"><span data-stu-id="3024b-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="3024b-108">Pour plus d’informations, consultez [opérations d’agrégation](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span><span class="sxs-lookup"><span data-stu-id="3024b-108">For more information, see [Aggregation Operations](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span></span>  
  
-   <span data-ttu-id="3024b-109">Vous ne pouvez pas appeler d'agrégats à l'aide de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="3024b-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="3024b-110">Les exemples des rubriques suivantes dérivent de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="3024b-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="3024b-111">Pour plus d’informations, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="3024b-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3024b-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3024b-112">In This Section</span></span>  
 [<span data-ttu-id="3024b-113">Retourner la valeur moyenne d’une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="3024b-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="3024b-114">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Average%2A>.</span><span class="sxs-lookup"><span data-stu-id="3024b-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="3024b-115">Dénombrer les éléments d’une séquence</span><span class="sxs-lookup"><span data-stu-id="3024b-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="3024b-116">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="3024b-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="3024b-117">Rechercher la valeur maximale dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="3024b-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="3024b-118">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="3024b-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="3024b-119">Rechercher la valeur minimale dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="3024b-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="3024b-120">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Min%2A>.</span><span class="sxs-lookup"><span data-stu-id="3024b-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="3024b-121">Calculer la somme de valeurs dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="3024b-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="3024b-122">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="3024b-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3024b-123">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="3024b-123">Related Sections</span></span>  
 [<span data-ttu-id="3024b-124">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="3024b-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="3024b-125">Fournit des liens vers les requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans Visual Basic et C#.</span><span class="sxs-lookup"><span data-stu-id="3024b-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="3024b-126">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="3024b-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="3024b-127">Fournit des liens vers des rubriques qui présentent des concepts pour la conception de requêtes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3024b-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="3024b-128">Introduction aux requêtes LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="3024b-128">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="3024b-129">Explique le fonctionnement des requêtes dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3024b-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
