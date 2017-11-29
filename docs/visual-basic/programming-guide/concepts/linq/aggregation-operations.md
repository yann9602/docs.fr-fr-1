---
title: "Opérations d’agrégation (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d4b07eeb1d09d7db0f75d96629c816f66dbb128
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="0fa03-102">Opérations d’agrégation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fa03-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="0fa03-103">Une opération d’agrégation calcule une valeur unique à partir d’une collection de valeurs.</span><span class="sxs-lookup"><span data-stu-id="0fa03-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="0fa03-104">Par exemple, une opération d'agrégation peut être le calcul de la température quotidienne moyenne à partir des valeurs de température quotidiennes relevées sur un mois.</span><span class="sxs-lookup"><span data-stu-id="0fa03-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="0fa03-105">L’illustration suivante montre les résultats de deux opérations d’agrégation différentes sur une séquence de nombres.</span><span class="sxs-lookup"><span data-stu-id="0fa03-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="0fa03-106">La première opération additionne les nombres.</span><span class="sxs-lookup"><span data-stu-id="0fa03-106">The first operation sums the numbers.</span></span> <span data-ttu-id="0fa03-107">La deuxième opération retourne la valeur maximale dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="0fa03-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="0fa03-108">![Opérations d’agrégation LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="0fa03-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="0fa03-109">Les méthodes d’opérateurs de requête standard qui effectuent des opérations d’agrégation sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="0fa03-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0fa03-110">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0fa03-110">Methods</span></span>  
  
|<span data-ttu-id="0fa03-111">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="0fa03-111">Method Name</span></span>|<span data-ttu-id="0fa03-112">Description</span><span class="sxs-lookup"><span data-stu-id="0fa03-112">Description</span></span>|<span data-ttu-id="0fa03-113">Syntaxe d’Expression de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0fa03-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="0fa03-114">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="0fa03-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="0fa03-115">Aggregate</span><span class="sxs-lookup"><span data-stu-id="0fa03-115">Aggregate</span></span>|<span data-ttu-id="0fa03-116">Effectue une opération d’agrégation personnalisée sur les valeurs d’une collection.</span><span class="sxs-lookup"><span data-stu-id="0fa03-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="0fa03-117">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="0fa03-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0fa03-118">Average</span><span class="sxs-lookup"><span data-stu-id="0fa03-118">Average</span></span>|<span data-ttu-id="0fa03-119">Calcule la valeur moyenne d’une collection de valeurs.</span><span class="sxs-lookup"><span data-stu-id="0fa03-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0fa03-120">Nombre</span><span class="sxs-lookup"><span data-stu-id="0fa03-120">Count</span></span>|<span data-ttu-id="0fa03-121">Compte tous les éléments d’une collection, ou uniquement les éléments basés sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="0fa03-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0fa03-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="0fa03-122">LongCount</span></span>|<span data-ttu-id="0fa03-123">Compte tous les éléments d’une grande collection, ou uniquement les éléments basés sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="0fa03-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0fa03-124">Max</span><span class="sxs-lookup"><span data-stu-id="0fa03-124">Max</span></span>|<span data-ttu-id="0fa03-125">Détermine la valeur maximale dans une collection.</span><span class="sxs-lookup"><span data-stu-id="0fa03-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0fa03-126">Min</span><span class="sxs-lookup"><span data-stu-id="0fa03-126">Min</span></span>|<span data-ttu-id="0fa03-127">Détermine la valeur minimale dans une collection.</span><span class="sxs-lookup"><span data-stu-id="0fa03-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0fa03-128">Sum</span><span class="sxs-lookup"><span data-stu-id="0fa03-128">Sum</span></span>|<span data-ttu-id="0fa03-129">Calcule la somme des valeurs d’une collection.</span><span class="sxs-lookup"><span data-stu-id="0fa03-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="0fa03-130">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="0fa03-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="0fa03-131">Average</span><span class="sxs-lookup"><span data-stu-id="0fa03-131">Average</span></span>  
 <span data-ttu-id="0fa03-132">Le code suivant exemple utilise le `Aggregate Into Average` clause dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour calculer la température moyenne dans un tableau de nombres qui représentent des températures.</span><span class="sxs-lookup"><span data-stu-id="0fa03-132">The following code example uses the `Aggregate Into Average` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a><span data-ttu-id="0fa03-133">Nombre</span><span class="sxs-lookup"><span data-stu-id="0fa03-133">Count</span></span>  
 <span data-ttu-id="0fa03-134">Le code suivant exemple utilise le `Aggregate Into Count` clause dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour compter le nombre de valeurs dans un tableau qui est supérieur ou égal à 80.</span><span class="sxs-lookup"><span data-stu-id="0fa03-134">The following code example uses the `Aggregate Into Count` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a><span data-ttu-id="0fa03-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="0fa03-135">LongCount</span></span>  
 <span data-ttu-id="0fa03-136">Le code suivant exemple utilise le `Aggregate Into LongCount` clause pour compter le nombre de valeurs dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="0fa03-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a><span data-ttu-id="0fa03-137">Max</span><span class="sxs-lookup"><span data-stu-id="0fa03-137">Max</span></span>  
 <span data-ttu-id="0fa03-138">Le code suivant exemple utilise le `Aggregate Into Max` clause pour calculer la température maximale dans un tableau de nombres qui représentent des températures.</span><span class="sxs-lookup"><span data-stu-id="0fa03-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a><span data-ttu-id="0fa03-139">Min</span><span class="sxs-lookup"><span data-stu-id="0fa03-139">Min</span></span>  
 <span data-ttu-id="0fa03-140">Le code suivant exemple utilise le `Aggregate Into Min` clause pour calculer la température minimale dans un tableau de nombres qui représentent des températures.</span><span class="sxs-lookup"><span data-stu-id="0fa03-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a><span data-ttu-id="0fa03-141">Sum</span><span class="sxs-lookup"><span data-stu-id="0fa03-141">Sum</span></span>  
 <span data-ttu-id="0fa03-142">Le code suivant exemple utilise le `Aggregate Into Sum` clause pour calculer le montant total de dépenses à partir d’un tableau de valeurs qui représentent des frais.</span><span class="sxs-lookup"><span data-stu-id="0fa03-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0fa03-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fa03-143">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="0fa03-144">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fa03-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="0fa03-145">Aggregate (clause)</span><span class="sxs-lookup"><span data-stu-id="0fa03-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="0fa03-146">Comment : calculer des valeurs de colonne dans un fichier de texte CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fa03-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [<span data-ttu-id="0fa03-147">Guide pratique : compter, additionner ou faire la moyenne de données</span><span class="sxs-lookup"><span data-stu-id="0fa03-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
 [<span data-ttu-id="0fa03-148">Guide pratique : rechercher la valeur minimale ou maximale dans un résultat de requête</span><span class="sxs-lookup"><span data-stu-id="0fa03-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
 [<span data-ttu-id="0fa03-149">Comment : interroger le plus grand nombre ou les fichiers dans une arborescence de répertoires (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fa03-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 [<span data-ttu-id="0fa03-150">Comment : rechercher le nombre Total d’octets dans un ensemble de dossiers (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fa03-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
