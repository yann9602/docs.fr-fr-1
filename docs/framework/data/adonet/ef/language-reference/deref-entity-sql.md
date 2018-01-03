---
title: DEREF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bade65b36363aef1597ce4664e3e514141dee908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="deref-entity-sql"></a><span data-ttu-id="30d4d-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="30d4d-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="30d4d-103">Déréférence une valeur de référence et génère le résultat de ce déréférencement.</span><span class="sxs-lookup"><span data-stu-id="30d4d-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30d4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30d4d-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="30d4d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="30d4d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="30d4d-106">Toute expression de requête valide qui retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="30d4d-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30d4d-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="30d4d-107">Return Value</span></span>  
 <span data-ttu-id="30d4d-108">Valeur de l'entité référencée.</span><span class="sxs-lookup"><span data-stu-id="30d4d-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30d4d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="30d4d-109">Remarks</span></span>  
 <span data-ttu-id="30d4d-110">L'opérateur DEREF déréférence une valeur de référence et génère le résultat de ce déréférencement.</span><span class="sxs-lookup"><span data-stu-id="30d4d-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="30d4d-111">Par exemple, si `r` est une référence de type ref\<T >, `Deref``(r)` est une expression de type `T` qui génère l’entité référencée par `r`.</span><span class="sxs-lookup"><span data-stu-id="30d4d-111">For example, if `r` is a reference of type ref\<T>, `Deref``(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="30d4d-112">Si la valeur de référence est null ou non résolue (autrement dit, la cible de la référence n'existe pas), le résultat de l'opérateur DEREF est null.</span><span class="sxs-lookup"><span data-stu-id="30d4d-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30d4d-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="30d4d-113">Example</span></span>  
 <span data-ttu-id="30d4d-114">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur DEREF pour déréférencer une valeur de référence et générer le résultat de ce déréférencement.</span><span class="sxs-lookup"><span data-stu-id="30d4d-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="30d4d-115">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="30d4d-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="30d4d-116">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="30d4d-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="30d4d-117">Suivez la procédure de [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="30d4d-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="30d4d-118">Passez à la méthode ExecutePrimitiveTypeQuery la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="30d4d-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="30d4d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30d4d-119">See Also</span></span>  
 [<span data-ttu-id="30d4d-120">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="30d4d-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="30d4d-121">REF</span><span class="sxs-lookup"><span data-stu-id="30d4d-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="30d4d-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="30d4d-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="30d4d-123">KEY</span><span class="sxs-lookup"><span data-stu-id="30d4d-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="30d4d-124">Types structurés autorisant la valeur null</span><span class="sxs-lookup"><span data-stu-id="30d4d-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
