---
title: "Opérations ensemblistes (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e30c521635326afeea4aad9ce932d5206d06c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="4a0bd-102">Opérations ensemblistes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a0bd-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="4a0bd-103">Les opérations ensemblistes dans LINQ font référence à des opérations de requête qui génèrent un jeu de résultats basé sur la présence ou l’absence d’éléments équivalents dans la même collection (ou le même ensemble) ou dans une collection distincte (ou un ensemble distinct).</span><span class="sxs-lookup"><span data-stu-id="4a0bd-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="4a0bd-104">Les méthodes d’opérateur de requête standard qui effectuent des opérations ensemblistes sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a0bd-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4a0bd-105">Methods</span></span>  
  
|<span data-ttu-id="4a0bd-106">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="4a0bd-106">Method Name</span></span>|<span data-ttu-id="4a0bd-107">Description</span><span class="sxs-lookup"><span data-stu-id="4a0bd-107">Description</span></span>|<span data-ttu-id="4a0bd-108">Syntaxe d’Expression de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a0bd-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="4a0bd-109">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="4a0bd-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="4a0bd-110">distinct</span><span class="sxs-lookup"><span data-stu-id="4a0bd-110">Distinct</span></span>|<span data-ttu-id="4a0bd-111">Supprime les valeurs en double d’une collection.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4a0bd-112">À l'exception</span><span class="sxs-lookup"><span data-stu-id="4a0bd-112">Except</span></span>|<span data-ttu-id="4a0bd-113">Retourne la différence ensembliste, à savoir les éléments d’une collection qui n’apparaissent pas dans une seconde collection.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="4a0bd-114">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4a0bd-115">Définir une intersection</span><span class="sxs-lookup"><span data-stu-id="4a0bd-115">Intersect</span></span>|<span data-ttu-id="4a0bd-116">Retourne l’intersection ensembliste, à savoir les éléments qui apparaissent dans chacune des deux collections.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="4a0bd-117">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4a0bd-118">Union</span><span class="sxs-lookup"><span data-stu-id="4a0bd-118">Union</span></span>|<span data-ttu-id="4a0bd-119">Retourne l’union ensembliste, à savoir les éléments uniques qui apparaissent dans l’une ou l’autre des deux collections.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="4a0bd-120">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="4a0bd-121">Comparaison d’opérations ensemblistes</span><span class="sxs-lookup"><span data-stu-id="4a0bd-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="4a0bd-122">distinct</span><span class="sxs-lookup"><span data-stu-id="4a0bd-122">Distinct</span></span>  
 <span data-ttu-id="4a0bd-123">L’illustration suivante représente le comportement de la méthode <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="4a0bd-124">La séquence retournée contient les éléments uniques de la séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="4a0bd-125">![Graphique illustrant le comportement de Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span><span class="sxs-lookup"><span data-stu-id="4a0bd-125">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="4a0bd-126">À l'exception</span><span class="sxs-lookup"><span data-stu-id="4a0bd-126">Except</span></span>  
 <span data-ttu-id="4a0bd-127">L’illustration suivante représente le comportement de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4a0bd-128">La séquence retournée contient uniquement les éléments de la première séquence d’entrée qui ne figurent pas dans la seconde séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="4a0bd-129">![Graphique montrant l’action de Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span><span class="sxs-lookup"><span data-stu-id="4a0bd-129">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="4a0bd-130">Définir une intersection</span><span class="sxs-lookup"><span data-stu-id="4a0bd-130">Intersect</span></span>  
 <span data-ttu-id="4a0bd-131">L’illustration suivante représente le comportement de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4a0bd-132">La séquence retournée contient les éléments qui sont communs aux deux séquences d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="4a0bd-133">![Graphique illustrant l’intersection de deux séquences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="4a0bd-133">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="4a0bd-134">Union</span><span class="sxs-lookup"><span data-stu-id="4a0bd-134">Union</span></span>  
 <span data-ttu-id="4a0bd-135">L’illustration suivante représente une opération d’union sur deux séquences de caractères.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="4a0bd-136">La séquence retournée contient les éléments uniques des deux séquences d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="4a0bd-137">![Graphique illustrant l’union de deux séquences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="4a0bd-137">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="4a0bd-138">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="4a0bd-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="4a0bd-139">L’exemple suivant utilise le `Distinct` clause dans une requête LINQ pour retourner les nombres uniques d’une liste d’entiers.</span><span class="sxs-lookup"><span data-stu-id="4a0bd-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4a0bd-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a0bd-140">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="4a0bd-141">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a0bd-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="4a0bd-142">Distinct (clause)</span><span class="sxs-lookup"><span data-stu-id="4a0bd-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="4a0bd-143">Comment : combiner et comparer des Collections de chaînes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a0bd-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [<span data-ttu-id="4a0bd-144">Comment : rechercher la différence définie entre deux listes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a0bd-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
