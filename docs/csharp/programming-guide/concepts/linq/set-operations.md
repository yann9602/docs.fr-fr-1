---
title: "Opérations ensemblistes (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5b546d9df8752fd7afd6e0db4525bc923a74bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-c"></a><span data-ttu-id="db9c2-102">Opérations ensemblistes (C#)</span><span class="sxs-lookup"><span data-stu-id="db9c2-102">Set Operations (C#)</span></span>
<span data-ttu-id="db9c2-103">Les opérations ensemblistes dans LINQ font référence à des opérations de requête qui génèrent un jeu de résultats basé sur la présence ou l’absence d’éléments équivalents dans la même collection (ou le même ensemble) ou dans une collection distincte (ou un ensemble distinct).</span><span class="sxs-lookup"><span data-stu-id="db9c2-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="db9c2-104">Les méthodes d’opérateur de requête standard qui effectuent des opérations ensemblistes sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="db9c2-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db9c2-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="db9c2-105">Methods</span></span>  
  
|<span data-ttu-id="db9c2-106">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="db9c2-106">Method Name</span></span>|<span data-ttu-id="db9c2-107">Description</span><span class="sxs-lookup"><span data-stu-id="db9c2-107">Description</span></span>|<span data-ttu-id="db9c2-108">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="db9c2-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="db9c2-109">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="db9c2-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="db9c2-110">distinct</span><span class="sxs-lookup"><span data-stu-id="db9c2-110">Distinct</span></span>|<span data-ttu-id="db9c2-111">Supprime les valeurs en double d’une collection.</span><span class="sxs-lookup"><span data-stu-id="db9c2-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="db9c2-112">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="db9c2-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="db9c2-113">À l'exception</span><span class="sxs-lookup"><span data-stu-id="db9c2-113">Except</span></span>|<span data-ttu-id="db9c2-114">Retourne la différence ensembliste, à savoir les éléments d’une collection qui n’apparaissent pas dans une seconde collection.</span><span class="sxs-lookup"><span data-stu-id="db9c2-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="db9c2-115">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="db9c2-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="db9c2-116">Définir une intersection</span><span class="sxs-lookup"><span data-stu-id="db9c2-116">Intersect</span></span>|<span data-ttu-id="db9c2-117">Retourne l’intersection ensembliste, à savoir les éléments qui apparaissent dans chacune des deux collections.</span><span class="sxs-lookup"><span data-stu-id="db9c2-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="db9c2-118">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="db9c2-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="db9c2-119">Union</span><span class="sxs-lookup"><span data-stu-id="db9c2-119">Union</span></span>|<span data-ttu-id="db9c2-120">Retourne l’union ensembliste, à savoir les éléments uniques qui apparaissent dans l’une ou l’autre des deux collections.</span><span class="sxs-lookup"><span data-stu-id="db9c2-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="db9c2-121">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="db9c2-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="db9c2-122">Comparaison d’opérations ensemblistes</span><span class="sxs-lookup"><span data-stu-id="db9c2-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="db9c2-123">distinct</span><span class="sxs-lookup"><span data-stu-id="db9c2-123">Distinct</span></span>  
 <span data-ttu-id="db9c2-124">L’illustration suivante représente le comportement de la méthode <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="db9c2-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="db9c2-125">La séquence retournée contient les éléments uniques de la séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="db9c2-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="db9c2-126">![Graphique illustrant le comportement de Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span><span class="sxs-lookup"><span data-stu-id="db9c2-126">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="db9c2-127">À l'exception</span><span class="sxs-lookup"><span data-stu-id="db9c2-127">Except</span></span>  
 <span data-ttu-id="db9c2-128">L’illustration suivante représente le comportement de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db9c2-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="db9c2-129">La séquence retournée contient uniquement les éléments de la première séquence d’entrée qui ne figurent pas dans la seconde séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="db9c2-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="db9c2-130">![Graphique montrant l’action de Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span><span class="sxs-lookup"><span data-stu-id="db9c2-130">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="db9c2-131">Définir une intersection</span><span class="sxs-lookup"><span data-stu-id="db9c2-131">Intersect</span></span>  
 <span data-ttu-id="db9c2-132">L’illustration suivante représente le comportement de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db9c2-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="db9c2-133">La séquence retournée contient les éléments qui sont communs aux deux séquences d’entrée.</span><span class="sxs-lookup"><span data-stu-id="db9c2-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="db9c2-134">![Graphique illustrant l’intersection de deux séquences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="db9c2-134">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="db9c2-135">Union</span><span class="sxs-lookup"><span data-stu-id="db9c2-135">Union</span></span>  
 <span data-ttu-id="db9c2-136">L’illustration suivante représente une opération d’union sur deux séquences de caractères.</span><span class="sxs-lookup"><span data-stu-id="db9c2-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="db9c2-137">La séquence retournée contient les éléments uniques des deux séquences d’entrée.</span><span class="sxs-lookup"><span data-stu-id="db9c2-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="db9c2-138">![Graphique illustrant l’union de deux séquences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="db9c2-138">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9c2-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db9c2-139">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="db9c2-140">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="db9c2-140">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="db9c2-141">Guide pratique pour combiner et comparer des collections de chaînes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="db9c2-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [<span data-ttu-id="db9c2-142">Guide pratique pour rechercher la différence ensembliste entre deux listes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="db9c2-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
