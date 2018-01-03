---
title: "Littéraux null et inférence de type (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5a8b921db06d600430fd4e10466070910119626d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="4b7b6-102">Littéraux null et inférence de type (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4b7b6-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="4b7b6-103">Les littéraux Null sont compatibles avec n'importe quel type dans le système de type [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4b7b6-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="4b7b6-104">Toutefois, pour le type d’un littéral null soit correctement déduit, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] impose certaines contraintes sur où un littéral null peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="4b7b6-105">Valeurs Null typées</span><span class="sxs-lookup"><span data-stu-id="4b7b6-105">Typed Nulls</span></span>  
 <span data-ttu-id="4b7b6-106">Les valeurs Null typées peuvent être utilisées dans n'importe quel contexte.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="4b7b6-107">L'inférence de type n'est pas requise pour les valeurs Null typées car leur type est connu.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="4b7b6-108">Par exemple, vous pouvez construire une valeur Null de type Int16 avec la construction [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivante :</span><span class="sxs-lookup"><span data-stu-id="4b7b6-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="4b7b6-109">Littéraux Null flottants</span><span class="sxs-lookup"><span data-stu-id="4b7b6-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="4b7b6-110">Les littéraux Null flottants peuvent être utilisés dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="4b7b6-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="4b7b6-111">En tant qu'argument d'une expression CAST ou TREAT.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="4b7b6-112">Il s'agit de la méthode recommandée pour produire une expression Null typée.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-112">This is the recommended way to produce a typed null expression.</span></span>  
  
-   <span data-ttu-id="4b7b6-113">En tant qu'argument d'une méthode ou d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-113">As an argument to a method or a function.</span></span> <span data-ttu-id="4b7b6-114">Les règles de surcharge standard s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-114">Standard overload rules apply.</span></span>  
  
-   <span data-ttu-id="4b7b6-115">En tant qu'un des arguments d'une expression arithmétique, telle que +, -, ou /.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="4b7b6-116">Les autres arguments ne peuvent pas être des littéraux Null, sinon l'inférence de type n'est pas possible.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
-   <span data-ttu-id="4b7b6-117">En tant qu'un des arguments d'une expression logique (AND, OR ou NOT).</span><span class="sxs-lookup"><span data-stu-id="4b7b6-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="4b7b6-118">Tous les arguments sont de type Boolean.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-118">All the arguments are known to be of type Boolean.</span></span>  
  
-   <span data-ttu-id="4b7b6-119">En tant qu'argument d'une expression IS NULL ou IS NOT NULL.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
-   <span data-ttu-id="4b7b6-120">En tant qu'un ou plusieurs des arguments d'une expression LIKE.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="4b7b6-121">Tous les arguments sont supposés être des chaînes.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-121">All arguments are expected to be strings.</span></span>  
  
-   <span data-ttu-id="4b7b6-122">En tant qu'un ou plusieurs des arguments d'un constructeur de type nommé.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
-   <span data-ttu-id="4b7b6-123">En tant qu'un ou plusieurs des arguments d'un constructeur de type multiset.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="4b7b6-124">Au moins, un argument du constructeur de type multiset doit être une expression qui n'est pas un littéral Null.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
-   <span data-ttu-id="4b7b6-125">En tant qu'une ou plusieurs des expressions THEN ou ELSE dans une expression CASE.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="4b7b6-126">Au moins l'une des expressions THEN ou ELSE dans l'expression CASE ne doit pas être un littéral Null.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="4b7b6-127">Les littéraux Null flottants ne peuvent pas être utilisés dans d'autres scénarios.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="4b7b6-128">Par exemple, ils ne peuvent pas être servir d’arguments à un constructeur de lignes.</span><span class="sxs-lookup"><span data-stu-id="4b7b6-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b7b6-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b7b6-129">See Also</span></span>  
 [<span data-ttu-id="4b7b6-130">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4b7b6-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
