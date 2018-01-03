---
title: "Exemples de requêtes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 91ff476ed8f6060975c6adc1fe01a6db9c199969
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="query-examples"></a><span data-ttu-id="9bc56-102">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="9bc56-102">Query Examples</span></span>
<span data-ttu-id="9bc56-103">Cette section fournit des exemples [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] et C# de requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] standard.</span><span class="sxs-lookup"><span data-stu-id="9bc56-103">This section provides [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="9bc56-104">Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent rechercher de nombreux autres exemples dans un exemple de solution disponible dans la section Exemples.</span><span class="sxs-lookup"><span data-stu-id="9bc56-104">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="9bc56-105">Pour plus d’informations, consultez [exemples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span><span class="sxs-lookup"><span data-stu-id="9bc56-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9bc56-106">*base de données* est souvent utilisée dans les exemples de code dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span><span class="sxs-lookup"><span data-stu-id="9bc56-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="9bc56-107">*base de données* est supposé pour être une instance d’un *Northwind* (classe), qui hérite de <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9bc56-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9bc56-108">In This Section</span></span>  
 [<span data-ttu-id="9bc56-109">Requêtes d’agrégation</span><span class="sxs-lookup"><span data-stu-id="9bc56-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="9bc56-110">Explique comment utiliser <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, etc.</span><span class="sxs-lookup"><span data-stu-id="9bc56-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="9bc56-111">Retourner le premier élément d’une séquence</span><span class="sxs-lookup"><span data-stu-id="9bc56-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="9bc56-112">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-113">Retourner ou ignorer des éléments d’une séquence</span><span class="sxs-lookup"><span data-stu-id="9bc56-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="9bc56-114">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Take%2A> et de <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-115">Trier les éléments d’une séquence</span><span class="sxs-lookup"><span data-stu-id="9bc56-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="9bc56-116">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-117">Regrouper des éléments dans une séquence</span><span class="sxs-lookup"><span data-stu-id="9bc56-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="9bc56-118">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-119">Éliminer des éléments en double d’une séquence</span><span class="sxs-lookup"><span data-stu-id="9bc56-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="9bc56-120">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-121">Déterminer si certains ou tous les éléments d’une séquence remplissent une condition</span><span class="sxs-lookup"><span data-stu-id="9bc56-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="9bc56-122">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.All%2A> et de <xref:System.Linq.Enumerable.Any%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-123">Concaténer deux séquences</span><span class="sxs-lookup"><span data-stu-id="9bc56-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="9bc56-124">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-125">Retourner la différence définie entre deux séquences</span><span class="sxs-lookup"><span data-stu-id="9bc56-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="9bc56-126">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Except%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-127">Retourner l’intersection définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="9bc56-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="9bc56-128">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Intersect%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-129">Retourner l’union définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="9bc56-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="9bc56-130">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Union%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-131">Convertir une séquence en tableau</span><span class="sxs-lookup"><span data-stu-id="9bc56-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="9bc56-132">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-133">Convertir une séquence en liste générique</span><span class="sxs-lookup"><span data-stu-id="9bc56-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="9bc56-134">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-135">Convertir un type en IEnumerable générique</span><span class="sxs-lookup"><span data-stu-id="9bc56-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="9bc56-136">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bc56-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="9bc56-137">Formuler des jointures et des requêtes de produit croisé</span><span class="sxs-lookup"><span data-stu-id="9bc56-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="9bc56-138">Fournit des exemples d'utilisation de la navigation de clé étrangère dans les clauses `from`, `where` et `select`.</span><span class="sxs-lookup"><span data-stu-id="9bc56-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="9bc56-139">Formuler des projections</span><span class="sxs-lookup"><span data-stu-id="9bc56-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="9bc56-140">Fournit des exemples de combinaison `select` avec d’autres fonctionnalités (par exemple, *types anonymes*) pour former des projections de requête.</span><span class="sxs-lookup"><span data-stu-id="9bc56-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9bc56-141">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9bc56-141">Related Sections</span></span>  
 [<span data-ttu-id="9bc56-142">Vue d’ensemble des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="9bc56-142">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 <span data-ttu-id="9bc56-143">Explique le concept d'opérateurs de requête standard.</span><span class="sxs-lookup"><span data-stu-id="9bc56-143">Explains the concept of standard query operators.</span></span>  
  
 [<span data-ttu-id="9bc56-144">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="9bc56-144">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="9bc56-145">Explique comment [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise des concepts qui s'appliquent aux requêtes.</span><span class="sxs-lookup"><span data-stu-id="9bc56-145">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="9bc56-146">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="9bc56-146">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="9bc56-147">Fournit un portail vers des rubriques qui expliquent des concepts de programmation en rapport avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bc56-147">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
