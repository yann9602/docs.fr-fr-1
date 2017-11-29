---
title: SET (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e70db99157e0bc49e1548d18c8fccfa44af42356
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="set-entity-sql"></a><span data-ttu-id="76361-102">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="76361-102">SET (Entity SQL)</span></span>
<span data-ttu-id="76361-103">L'expression SET est utilisée pour convertir une collection d'objets en ensemble grâce à la production d'une nouvelle collection dans laquelle toutes les éléments en double ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="76361-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76361-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76361-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="76361-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="76361-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="76361-106">Toute expression de requête valide qui retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="76361-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76361-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="76361-107">Remarks</span></span>  
 <span data-ttu-id="76361-108">L'expression d'ensemble `SET(c)` est logiquement équivalente à l'instruction select suivante :</span><span class="sxs-lookup"><span data-stu-id="76361-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="76361-109">`SET` est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="76361-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="76361-110">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="76361-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="76361-111">Consultez [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pour des informations de priorité pour la [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateurs de jeu.</span><span class="sxs-lookup"><span data-stu-id="76361-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76361-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="76361-112">Example</span></span>  
 <span data-ttu-id="76361-113">La requête Entity SQL ci-dessous utilise l'expression SET pour convertir une collection d'objets en ensemble.</span><span class="sxs-lookup"><span data-stu-id="76361-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="76361-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="76361-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="76361-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="76361-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="76361-116">Suivez la procédure de [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="76361-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="76361-117">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="76361-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="76361-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76361-118">See Also</span></span>  
 [<span data-ttu-id="76361-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="76361-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
