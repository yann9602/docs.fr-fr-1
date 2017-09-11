---
title: "Partitionnement des données (C#)"
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
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
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
ms.openlocfilehash: 2f1690dac93d5e74f1305bd457f8bc749bec5449
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="partitioning-data-c"></a><span data-ttu-id="e0744-102">Partitionnement des données (C#)</span><span class="sxs-lookup"><span data-stu-id="e0744-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="e0744-103">Le partitionnement dans LINQ désigne l’opération consistant à diviser une séquence d’entrée en deux sections, sans réorganiser les éléments, puis à retourner l’une des sections.</span><span class="sxs-lookup"><span data-stu-id="e0744-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="e0744-104">L’illustration suivante montre les résultats de trois opérations de partitionnement différentes sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="e0744-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="e0744-105">La première opération retourne les trois premiers éléments de la séquence.</span><span class="sxs-lookup"><span data-stu-id="e0744-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="e0744-106">La deuxième opération ignore les trois premiers éléments et retourne les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="e0744-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="e0744-107">La troisième opération ignore les deux premiers éléments de la séquence et retourne les trois éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="e0744-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="e0744-108">![Opérations de partitionnement LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="e0744-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="e0744-109">Les méthodes d’opérateurs de requête standard qui partitionnent des séquences sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="e0744-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="e0744-110">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="e0744-110">Operators</span></span>  
  
|<span data-ttu-id="e0744-111">Nom d'opérateur</span><span class="sxs-lookup"><span data-stu-id="e0744-111">Operator Name</span></span>|<span data-ttu-id="e0744-112">Description</span><span class="sxs-lookup"><span data-stu-id="e0744-112">Description</span></span>|<span data-ttu-id="e0744-113">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="e0744-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="e0744-114">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="e0744-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e0744-115">Ignorer</span><span class="sxs-lookup"><span data-stu-id="e0744-115">Skip</span></span>|<span data-ttu-id="e0744-116">Ignore les éléments jusqu’à une position spécifiée dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="e0744-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="e0744-117">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="e0744-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|<span data-ttu-id="e0744-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="e0744-118">SkipWhile</span></span>|<span data-ttu-id="e0744-119">Ignore les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.</span><span class="sxs-lookup"><span data-stu-id="e0744-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="e0744-120">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="e0744-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|<span data-ttu-id="e0744-121">Take</span><span class="sxs-lookup"><span data-stu-id="e0744-121">Take</span></span>|<span data-ttu-id="e0744-122">Prend les éléments jusqu’à une position spécifiée dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="e0744-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="e0744-123">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="e0744-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|<span data-ttu-id="e0744-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="e0744-124">TakeWhile</span></span>|<span data-ttu-id="e0744-125">Prend les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.</span><span class="sxs-lookup"><span data-stu-id="e0744-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="e0744-126">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="e0744-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="e0744-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0744-127">See Also</span></span>  
 <span data-ttu-id="e0744-128"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="e0744-128"><xref:System.Linq></span></span>   
 [<span data-ttu-id="e0744-129">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="e0744-129">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

