---
title: "Opérations de quantificateur (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d6152cbbd390508a8ffce732f6cbdf1f2e1aa0f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="80ffc-102">Opérations de quantificateur (C#)</span><span class="sxs-lookup"><span data-stu-id="80ffc-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="80ffc-103">Les opérations de quantificateur retournent une valeur <xref:System.Boolean> qui indique si certains ou tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="80ffc-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="80ffc-104">L’illustration suivante représente deux opérations de quantificateur différentes sur deux séquences sources différentes.</span><span class="sxs-lookup"><span data-stu-id="80ffc-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="80ffc-105">La première opération demande si un ou plusieurs des éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="80ffc-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="80ffc-106">La deuxième opération demande si tous les éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="80ffc-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="80ffc-107">![Opérations de quantificateur LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "Quantificateur_LINQ")</span><span class="sxs-lookup"><span data-stu-id="80ffc-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="80ffc-108">Les méthodes d’opérateur de requête standard qui effectuent des opérations de quantificateur sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="80ffc-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80ffc-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="80ffc-109">Methods</span></span>  
  
|<span data-ttu-id="80ffc-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="80ffc-110">Method Name</span></span>|<span data-ttu-id="80ffc-111">Description</span><span class="sxs-lookup"><span data-stu-id="80ffc-111">Description</span></span>|<span data-ttu-id="80ffc-112">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="80ffc-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="80ffc-113">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="80ffc-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="80ffc-114">Tout</span><span class="sxs-lookup"><span data-stu-id="80ffc-114">All</span></span>|<span data-ttu-id="80ffc-115">Détermine si tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="80ffc-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="80ffc-116">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="80ffc-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="80ffc-117">Any</span><span class="sxs-lookup"><span data-stu-id="80ffc-117">Any</span></span>|<span data-ttu-id="80ffc-118">Détermine si certains éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="80ffc-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="80ffc-119">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="80ffc-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="80ffc-120">Contient</span><span class="sxs-lookup"><span data-stu-id="80ffc-120">Contains</span></span>|<span data-ttu-id="80ffc-121">Détermine si une séquence contient un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="80ffc-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="80ffc-122">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="80ffc-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="80ffc-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80ffc-123">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="80ffc-124">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="80ffc-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="80ffc-125">Guide pratique pour spécifier dynamiquement des filtres de prédicat au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="80ffc-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [<span data-ttu-id="80ffc-126">Guide pratique pour rechercher des phrases qui contiennent un groupe de mots spécifié (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="80ffc-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
