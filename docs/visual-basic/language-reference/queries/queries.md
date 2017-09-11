---
title: "Requêtes (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic]
- LINQ, queries
ms.assetid: 8edc717c-4a24-4cbc-9c16-11f479c935db
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4a178714055076537033fbda32d7c7c1c544351d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="queries-visual-basic"></a><span data-ttu-id="c0bf9-102">Requêtes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-102">Queries (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="c0bf9-103">Vous pouvez ainsi créer [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions dans votre code.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-103"> enables you to create [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0bf9-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c0bf9-104">In This Section</span></span>  
 [<span data-ttu-id="c0bf9-105">Aggregate (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-105">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 <span data-ttu-id="c0bf9-106">Décrit le `Aggregate` clause, qui applique une ou plusieurs fonctions d’agrégation à une collection.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-106">Describes the `Aggregate` clause, which applies one or more aggregate functions to a collection.</span></span>  
  
 [<span data-ttu-id="c0bf9-107">Distinct (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-107">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 <span data-ttu-id="c0bf9-108">Décrit le `Distinct` clause, qui restreint les valeurs de la variable de portée actuelle pour éliminer les doublons dans les résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-108">Describes the `Distinct` clause, which restricts the values of the current range variable to eliminate duplicate values in query results.</span></span>  
  
 [<span data-ttu-id="c0bf9-109">From (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-109">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 <span data-ttu-id="c0bf9-110">Décrit le `From` clause qui spécifie une collection et une variable de portée pour une requête.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-110">Describes the `From` clause, which specifies a collection and a range variable for a query.</span></span>  
  
 [<span data-ttu-id="c0bf9-111">Group By (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-111">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)  
 <span data-ttu-id="c0bf9-112">Décrit le `Group By` clause, qui regroupe les éléments d’un résultat de requête et peut être utilisé pour appliquer des fonctions d’agrégation à chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-112">Describes the `Group By` clause, which groups the elements of a query result and can be used to apply aggregate functions to each group.</span></span>  
  
 [<span data-ttu-id="c0bf9-113">Group Join (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-113">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 <span data-ttu-id="c0bf9-114">Décrit le `Group Join` clause, qui combine deux collections en une collection hiérarchique unique.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-114">Describes the `Group Join` clause, which combines two collections into a single hierarchical collection.</span></span>  
  
 [<span data-ttu-id="c0bf9-115">Join (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-115">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 <span data-ttu-id="c0bf9-116">Décrit le `Join` clause, qui combine deux collections en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-116">Describes the `Join` clause, which combines two collections into a single collection.</span></span>  
  
 [<span data-ttu-id="c0bf9-117">Let (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-117">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 <span data-ttu-id="c0bf9-118">Décrit le `Let` clause, qui calcule une valeur et l’assigne à une variable dans la requête.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-118">Describes the `Let` clause, which computes a value and assigns it to a new variable in the query.</span></span>  
  
 [<span data-ttu-id="c0bf9-119">Order By (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-119">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 <span data-ttu-id="c0bf9-120">Décrit le `Order By` clause qui spécifie l’ordre de tri pour les colonnes dans une requête.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-120">Describes the `Order By` clause, which specifies the sort order for columns in a query.</span></span>  
  
 [<span data-ttu-id="c0bf9-121">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-121">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 <span data-ttu-id="c0bf9-122">Décrit le `Select` clause qui déclare un jeu de variables de portée pour une requête.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-122">Describes the `Select` clause, which declares a set of range variables for a query.</span></span>  
  
 [<span data-ttu-id="c0bf9-123">Skip (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-123">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 <span data-ttu-id="c0bf9-124">Décrit le `Skip` clause, qui ignore un nombre spécifié d’éléments dans une collection, puis retourne les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-124">Describes the `Skip` clause, which bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
 [<span data-ttu-id="c0bf9-125">Skip While (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 <span data-ttu-id="c0bf9-126">Décrit la `Skip While` clause, qui ignore les éléments d’une collection tant qu’une condition spécifiée est `true` , puis retourne les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-126">Describes the `Skip While` clause, which bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
 [<span data-ttu-id="c0bf9-127">Take (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-127">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 <span data-ttu-id="c0bf9-128">Décrit le `Take` clause, qui retourne un nombre spécifié d’éléments contigus à partir du début d’une collection.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-128">Describes the `Take` clause, which returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
 [<span data-ttu-id="c0bf9-129">Take While (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-129">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 <span data-ttu-id="c0bf9-130">Décrit la `Take While` clause qui inclut les éléments d’une collection tant qu’une condition spécifiée est `true` et ignore les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-130">Describes the `Take While` clause, which includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
 [<span data-ttu-id="c0bf9-131">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-131">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 <span data-ttu-id="c0bf9-132">Décrit le `Where` clause qui spécifie une condition de filtrage pour une requête.</span><span class="sxs-lookup"><span data-stu-id="c0bf9-132">Describes the `Where` clause, which specifies a filtering condition for a query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0bf9-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0bf9-133">See Also</span></span>  
 <span data-ttu-id="c0bf9-134">[LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0bf9-134">[LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="c0bf9-135"> [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="c0bf9-135"> [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
