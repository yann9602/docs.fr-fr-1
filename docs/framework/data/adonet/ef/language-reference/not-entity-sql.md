---
title: '! (NOT) (Entity SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f10e65e284a14d6d86f9722cf44f080321fa0b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="-not-entity-sql"></a><span data-ttu-id="9df83-103">!</span><span class="sxs-lookup"><span data-stu-id="9df83-103">!</span></span> <span data-ttu-id="9df83-104">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9df83-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="9df83-105">Inverse une expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="9df83-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df83-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9df83-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9df83-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="9df83-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="9df83-108">Toute expression valide qui retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="9df83-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9df83-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="9df83-109">Remarks</span></span>  
 <span data-ttu-id="9df83-110">Le point d'exclamation (!) a la même fonctionnalité que l'opérateur NOT.</span><span class="sxs-lookup"><span data-stu-id="9df83-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9df83-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="9df83-111">Example</span></span>  
 <span data-ttu-id="9df83-112">La requête Entity SQL ci-dessous utilise l'opérateur NOT pour inverser une expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="9df83-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="9df83-113">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="9df83-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9df83-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9df83-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9df83-115">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9df83-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="9df83-116">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="9df83-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="9df83-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9df83-117">See Also</span></span>  
 [<span data-ttu-id="9df83-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9df83-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
