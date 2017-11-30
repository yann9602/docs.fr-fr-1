---
title: THEN (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 99fd941c963ff87203d7b315beb606d40001224d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="then-entity-sql"></a><span data-ttu-id="4a039-102">THEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4a039-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="4a039-103">Résultat d'une clause WHEN lorsqu'elle prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="4a039-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a039-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a039-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a039-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a039-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="4a039-106">Toute expression booléenne valide.</span><span class="sxs-lookup"><span data-stu-id="4a039-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="4a039-107">Toute expression de requête valide qui retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="4a039-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a039-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="4a039-108">Remarks</span></span>  
 <span data-ttu-id="4a039-109">Si `when_expression` prend la valeur `true`, le résultat est l'expression `then-expression`correspondante.</span><span class="sxs-lookup"><span data-stu-id="4a039-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="4a039-110">Si aucune des conditions WHEN n'est remplie, `else-expression` est évaluée.</span><span class="sxs-lookup"><span data-stu-id="4a039-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="4a039-111">Toutefois, en l'absence d'une expression `else-expression`, le résultat est Null.</span><span class="sxs-lookup"><span data-stu-id="4a039-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="4a039-112">Pour obtenir un exemple, consultez [cas](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4a039-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a039-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="4a039-113">Example</span></span>  
 <span data-ttu-id="4a039-114">La requête Entity SQL ci-dessous utilise l'expression CASE pour évaluer un ensemble d'expressions `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="4a039-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="4a039-115">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="4a039-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4a039-116">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4a039-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4a039-117">Suivez la procédure de [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4a039-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="4a039-118">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="4a039-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="4a039-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a039-119">See Also</span></span>  
 [<span data-ttu-id="4a039-120">CAS</span><span class="sxs-lookup"><span data-stu-id="4a039-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [<span data-ttu-id="4a039-121">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4a039-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
