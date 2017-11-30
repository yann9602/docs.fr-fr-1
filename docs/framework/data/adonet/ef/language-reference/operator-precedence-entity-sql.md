---
title: "Priorité des opérateurs (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 484eedffeaffb625cd43352dadedb8c99fbc65ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="bac52-102">Priorité des opérateurs (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bac52-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="bac52-103">Lorsqu’un [!INCLUDE[esql](../../../../../../includes/esql-md.md)] requête comporte plusieurs opérateurs, la priorité des opérateurs détermine l’ordre dans lequel les opérations sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="bac52-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="bac52-104">Cet ordre peut affecter considérablement le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="bac52-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="bac52-105">L'ordre de priorité des opérateurs est indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="bac52-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="bac52-106">Un opérateur avec un haut niveau de priorité est évalué avant un opérateur avec un faible niveau de priorité.</span><span class="sxs-lookup"><span data-stu-id="bac52-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="bac52-107">Niveau</span><span class="sxs-lookup"><span data-stu-id="bac52-107">Level</span></span>|<span data-ttu-id="bac52-108">Type d'opération</span><span class="sxs-lookup"><span data-stu-id="bac52-108">Operation type</span></span>|<span data-ttu-id="bac52-109">Opérateur</span><span class="sxs-lookup"><span data-stu-id="bac52-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="bac52-110">1</span><span class="sxs-lookup"><span data-stu-id="bac52-110">1</span></span>|<span data-ttu-id="bac52-111">Principale</span><span class="sxs-lookup"><span data-stu-id="bac52-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="bac52-112">2</span><span class="sxs-lookup"><span data-stu-id="bac52-112">2</span></span>|<span data-ttu-id="bac52-113">Unaire</span><span class="sxs-lookup"><span data-stu-id="bac52-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="bac52-114">3</span><span class="sxs-lookup"><span data-stu-id="bac52-114">3</span></span>|<span data-ttu-id="bac52-115">Multiplication</span><span class="sxs-lookup"><span data-stu-id="bac52-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="bac52-116">4</span><span class="sxs-lookup"><span data-stu-id="bac52-116">4</span></span>|<span data-ttu-id="bac52-117">Addition</span><span class="sxs-lookup"><span data-stu-id="bac52-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="bac52-118">5</span><span class="sxs-lookup"><span data-stu-id="bac52-118">5</span></span>|<span data-ttu-id="bac52-119">Classement</span><span class="sxs-lookup"><span data-stu-id="bac52-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="bac52-120">6</span><span class="sxs-lookup"><span data-stu-id="bac52-120">6</span></span>|<span data-ttu-id="bac52-121">Égalité</span><span class="sxs-lookup"><span data-stu-id="bac52-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="bac52-122">7</span><span class="sxs-lookup"><span data-stu-id="bac52-122">7</span></span>|<span data-ttu-id="bac52-123">AND conditionnel</span><span class="sxs-lookup"><span data-stu-id="bac52-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="bac52-124">8</span><span class="sxs-lookup"><span data-stu-id="bac52-124">8</span></span>|<span data-ttu-id="bac52-125">OR conditionnel</span><span class="sxs-lookup"><span data-stu-id="bac52-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="bac52-126">Lorsque deux opérateurs dans une expression ont le même niveau de priorité, ils sont évalués de gauche à droite, en fonction de leur position dans la requête.</span><span class="sxs-lookup"><span data-stu-id="bac52-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="bac52-127">Par exemple, `x+y-z` est évalué comme étant `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="bac52-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="bac52-128">Vous pouvez utiliser des parenthèses pour modifier la priorité habituelle des opérateurs dans une requête.</span><span class="sxs-lookup"><span data-stu-id="bac52-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="bac52-129">Tout ce qui se trouve entre parenthèses est évalué en premier pour produire un seul résultat, qui est ensuite utilisé par un opérateur en dehors des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="bac52-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="bac52-130">Par exemple, `x+y*z` multiplie `y` par `z` , puis ajoute `x`, mais `(x+y)*z` ajoute `x` à `y` , puis multiplie le résultat par `z`.</span><span class="sxs-lookup"><span data-stu-id="bac52-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac52-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bac52-131">See Also</span></span>  
 [<span data-ttu-id="bac52-132">Vue d’ensemble de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bac52-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
