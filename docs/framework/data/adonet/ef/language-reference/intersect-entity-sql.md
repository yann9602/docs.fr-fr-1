---
title: INTERSECT (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 70078c849e78ff31d3d55c12606d8423d4e6772f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="6637a-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6637a-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="6637a-103">Retourne une collection de valeurs distinctes qui sont retournées par les expressions de requête tant à gauche qu'à droite de l'opérande INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="6637a-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="6637a-104">Toutes les expressions doivent être du même type que le `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="6637a-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6637a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6637a-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6637a-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="6637a-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6637a-107">Toute expression de requête valide qui retourne une collection à comparer avec la collection retournée par une autre expression de requête.</span><span class="sxs-lookup"><span data-stu-id="6637a-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6637a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6637a-108">Return Value</span></span>  
 <span data-ttu-id="6637a-109">Collection du même type que l' `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="6637a-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6637a-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="6637a-110">Remarks</span></span>  
 <span data-ttu-id="6637a-111">INTERSECT est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6637a-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="6637a-112">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="6637a-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="6637a-113">Pour plus d’informations de priorité pour la [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateurs de jeu, consultez [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6637a-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6637a-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="6637a-114">Example</span></span>  
 <span data-ttu-id="6637a-115">La requête Entity SQL ci-dessous utilise l'opérateur INTERSECT pour retourner une collection de valeurs distinctes qui sont retournées par les expressions de requête tant à gauche qu'à droite de l'opérande INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="6637a-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="6637a-116">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="6637a-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6637a-117">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6637a-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6637a-118">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6637a-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6637a-119">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="6637a-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="6637a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6637a-120">See Also</span></span>  
 [<span data-ttu-id="6637a-121">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6637a-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
