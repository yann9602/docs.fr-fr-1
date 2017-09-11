---
title: "Opérations d’éléments (C#)"
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
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
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
ms.openlocfilehash: da747e884960c89fabc45d3761da92f913d66362
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="element-operations-c"></a><span data-ttu-id="adb94-102">Opérations d’éléments (C#)</span><span class="sxs-lookup"><span data-stu-id="adb94-102">Element Operations (C#)</span></span>
<span data-ttu-id="adb94-103">Les opérations d’éléments retournent un élément unique et spécifique à partir d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="adb94-103">Element operations return a single, specific element from a sequence.</span></span>  
  
 <span data-ttu-id="adb94-104">Les méthodes d’opérateurs de requête standard qui effectuent des opérations d’éléments sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="adb94-104">The standard query operator methods that perform element operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="adb94-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="adb94-105">Methods</span></span>  
  
|<span data-ttu-id="adb94-106">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="adb94-106">Method Name</span></span>|<span data-ttu-id="adb94-107">Description</span><span class="sxs-lookup"><span data-stu-id="adb94-107">Description</span></span>|<span data-ttu-id="adb94-108">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="adb94-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="adb94-109">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="adb94-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="adb94-110">ElementAt</span><span class="sxs-lookup"><span data-stu-id="adb94-110">ElementAt</span></span>|<span data-ttu-id="adb94-111">Retourne l’élément situé à un index spécifié dans une collection.</span><span class="sxs-lookup"><span data-stu-id="adb94-111">Returns the element at a specified index in a collection.</span></span>|<span data-ttu-id="adb94-112">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="adb94-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>|  
|<span data-ttu-id="adb94-113">ElementAtOrDefault</span><span class="sxs-lookup"><span data-stu-id="adb94-113">ElementAtOrDefault</span></span>|<span data-ttu-id="adb94-114">Retourne l’élément situé à un index spécifié dans une collection ou une valeur par défaut si l’index est hors limites.</span><span class="sxs-lookup"><span data-stu-id="adb94-114">Returns the element at a specified index in a collection or a default value if the index is out of range.</span></span>|<span data-ttu-id="adb94-115">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="adb94-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>|  
|<span data-ttu-id="adb94-116">First</span><span class="sxs-lookup"><span data-stu-id="adb94-116">First</span></span>|<span data-ttu-id="adb94-117">Retourne le premier élément d’une collection ou le premier élément qui satisfait à une condition.</span><span class="sxs-lookup"><span data-stu-id="adb94-117">Returns the first element of a collection, or the first element that satisfies a condition.</span></span>|<span data-ttu-id="adb94-118">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="adb94-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=fullName>|  
|<span data-ttu-id="adb94-119">FirstOrDefault</span><span class="sxs-lookup"><span data-stu-id="adb94-119">FirstOrDefault</span></span>|<span data-ttu-id="adb94-120">Retourne le premier élément d’une collection ou le premier élément qui remplit une condition.</span><span class="sxs-lookup"><span data-stu-id="adb94-120">Returns the first element of a collection, or the first element that satisfies a condition.</span></span> <span data-ttu-id="adb94-121">Retourne une valeur par défaut s’il n’existe aucun élément répondant aux critères.</span><span class="sxs-lookup"><span data-stu-id="adb94-121">Returns a default value if no such element exists.</span></span>|<span data-ttu-id="adb94-122">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="adb94-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=fullName>|  
|<span data-ttu-id="adb94-123">Dernier</span><span class="sxs-lookup"><span data-stu-id="adb94-123">Last</span></span>|<span data-ttu-id="adb94-124">Retourne le dernier élément d’une collection ou le dernier élément qui remplit une condition.</span><span class="sxs-lookup"><span data-stu-id="adb94-124">Returns the last element of a collection, or the last element that satisfies a condition.</span></span>|<span data-ttu-id="adb94-125">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="adb94-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Last%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=fullName>|  
|<span data-ttu-id="adb94-126">LastOrDefault</span><span class="sxs-lookup"><span data-stu-id="adb94-126">LastOrDefault</span></span>|<span data-ttu-id="adb94-127">Retourne le dernier élément d’une collection ou le dernier élément qui remplit une condition.</span><span class="sxs-lookup"><span data-stu-id="adb94-127">Returns the last element of a collection, or the last element that satisfies a condition.</span></span> <span data-ttu-id="adb94-128">Retourne une valeur par défaut s’il n’existe aucun élément répondant aux critères.</span><span class="sxs-lookup"><span data-stu-id="adb94-128">Returns a default value if no such element exists.</span></span>|<span data-ttu-id="adb94-129">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="adb94-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>|  
|<span data-ttu-id="adb94-130">Single</span><span class="sxs-lookup"><span data-stu-id="adb94-130">Single</span></span>|<span data-ttu-id="adb94-131">Retourne le seul élément d’une collection ou le seul élément qui remplit une condition.</span><span class="sxs-lookup"><span data-stu-id="adb94-131">Returns the only element of a collection, or the only element that satisfies a condition.</span></span>|<span data-ttu-id="adb94-132">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="adb94-132">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=fullName>|  
|<span data-ttu-id="adb94-133">SingleOrDefault</span><span class="sxs-lookup"><span data-stu-id="adb94-133">SingleOrDefault</span></span>|<span data-ttu-id="adb94-134">Retourne le seul élément d’une collection ou le seul élément qui remplit une condition.</span><span class="sxs-lookup"><span data-stu-id="adb94-134">Returns the only element of a collection, or the only element that satisfies a condition.</span></span> <span data-ttu-id="adb94-135">Retourne une valeur par défaut s’il n’existe aucun élément remplissant les critères ou si la collection ne contient pas exactement un élément.</span><span class="sxs-lookup"><span data-stu-id="adb94-135">Returns a default value if no such element exists or the collection does not contain exactly one element.</span></span>|<span data-ttu-id="adb94-136">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="adb94-136">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="adb94-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adb94-137">See Also</span></span>  
 <span data-ttu-id="adb94-138"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="adb94-138"><xref:System.Linq></span></span>   
 <span data-ttu-id="adb94-139">[Présentation des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="adb94-139">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 [<span data-ttu-id="adb94-140">Guide pratique pour interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="adb94-140">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)

