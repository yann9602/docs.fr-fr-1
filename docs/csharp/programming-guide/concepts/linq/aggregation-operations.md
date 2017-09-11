---
title: "Opérations d’agrégation (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6c453bdccdb3af026fe4f4fb79c6e33e44e7a8f0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="aggregation-operations-c"></a><span data-ttu-id="4ffdc-102">Opérations d’agrégation (C#)</span><span class="sxs-lookup"><span data-stu-id="4ffdc-102">Aggregation Operations (C#)</span></span>
<span data-ttu-id="4ffdc-103">Une opération d’agrégation calcule une valeur unique à partir d’une collection de valeurs.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="4ffdc-104">Par exemple, une opération d'agrégation peut être le calcul de la température quotidienne moyenne à partir des valeurs de température quotidiennes relevées sur un mois.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="4ffdc-105">L’illustration suivante montre les résultats de deux opérations d’agrégation différentes sur une séquence de nombres.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="4ffdc-106">La première opération additionne les nombres.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-106">The first operation sums the numbers.</span></span> <span data-ttu-id="4ffdc-107">La deuxième opération retourne la valeur maximale dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="4ffdc-108">![Opérations d’agrégation LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="4ffdc-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="4ffdc-109">Les méthodes d’opérateurs de requête standard qui effectuent des opérations d’agrégation sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4ffdc-110">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4ffdc-110">Methods</span></span>  
  
|<span data-ttu-id="4ffdc-111">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="4ffdc-111">Method Name</span></span>|<span data-ttu-id="4ffdc-112">Description</span><span class="sxs-lookup"><span data-stu-id="4ffdc-112">Description</span></span>|<span data-ttu-id="4ffdc-113">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="4ffdc-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="4ffdc-114">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="4ffdc-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="4ffdc-115">Aggregate</span><span class="sxs-lookup"><span data-stu-id="4ffdc-115">Aggregate</span></span>|<span data-ttu-id="4ffdc-116">Effectue une opération d’agrégation personnalisée sur les valeurs d’une collection.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="4ffdc-117">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=fullName>|  
|<span data-ttu-id="4ffdc-118">Average</span><span class="sxs-lookup"><span data-stu-id="4ffdc-118">Average</span></span>|<span data-ttu-id="4ffdc-119">Calcule la valeur moyenne d’une collection de valeurs.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-119">Calculates the average value of a collection of values.</span></span>|<span data-ttu-id="4ffdc-120">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Average%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=fullName>|  
|<span data-ttu-id="4ffdc-121">Nombre</span><span class="sxs-lookup"><span data-stu-id="4ffdc-121">Count</span></span>|<span data-ttu-id="4ffdc-122">Compte tous les éléments d’une collection, ou uniquement les éléments basés sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-122">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="4ffdc-123">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=fullName>|  
|<span data-ttu-id="4ffdc-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="4ffdc-124">LongCount</span></span>|<span data-ttu-id="4ffdc-125">Compte tous les éléments d’une grande collection, ou uniquement les éléments basés sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-125">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="4ffdc-126">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=fullName>|  
|<span data-ttu-id="4ffdc-127">Max</span><span class="sxs-lookup"><span data-stu-id="4ffdc-127">Max</span></span>|<span data-ttu-id="4ffdc-128">Détermine la valeur maximale dans une collection.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-128">Determines the maximum value in a collection.</span></span>|<span data-ttu-id="4ffdc-129">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Max%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>|  
|<span data-ttu-id="4ffdc-130">Min</span><span class="sxs-lookup"><span data-stu-id="4ffdc-130">Min</span></span>|<span data-ttu-id="4ffdc-131">Détermine la valeur minimale dans une collection.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-131">Determines the minimum value in a collection.</span></span>|<span data-ttu-id="4ffdc-132">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-132">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Min%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>|  
|<span data-ttu-id="4ffdc-133">Sum</span><span class="sxs-lookup"><span data-stu-id="4ffdc-133">Sum</span></span>|<span data-ttu-id="4ffdc-134">Calcule la somme des valeurs d’une collection.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-134">Calculates the sum of the values in a collection.</span></span>|<span data-ttu-id="4ffdc-135">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4ffdc-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="4ffdc-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ffdc-136">See Also</span></span>  
 <span data-ttu-id="4ffdc-137"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="4ffdc-137"><xref:System.Linq></span></span>   
 <span data-ttu-id="4ffdc-138">[Présentation des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4ffdc-138">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="4ffdc-139">[Guide pratique pour calculer des valeurs de colonnes dans un fichier texte CSV (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md) </span><span class="sxs-lookup"><span data-stu-id="4ffdc-139">[How to: Compute Column Values in a CSV Text File (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md) </span></span>  
 <span data-ttu-id="4ffdc-140">[Guide pratique pour rechercher le ou les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md) </span><span class="sxs-lookup"><span data-stu-id="4ffdc-140">[How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md) </span></span>  
 [<span data-ttu-id="4ffdc-141">Guide pratique pour rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4ffdc-141">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)

