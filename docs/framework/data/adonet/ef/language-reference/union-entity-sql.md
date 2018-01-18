---
title: UNION (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 067c3fedb1e03741158209751de9a13a00c23c35
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="union-entity-sql"></a><span data-ttu-id="8f55b-102">UNION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8f55b-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="8f55b-103">Combine les résultats de deux requêtes, ou plus, en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="8f55b-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f55b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f55b-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f55b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8f55b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8f55b-106">Toute expression de requête valide qui retourne une collection à combiner à la collection. Toutes les expressions doivent être du même type que la valeur `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="8f55b-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="8f55b-107">UNION</span><span class="sxs-lookup"><span data-stu-id="8f55b-107">UNION</span></span>  
 <span data-ttu-id="8f55b-108">Spécifie que plusieurs collections doivent être combinées et retournées sous la forme d'une collection unique.</span><span class="sxs-lookup"><span data-stu-id="8f55b-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="8f55b-109">ALL</span><span class="sxs-lookup"><span data-stu-id="8f55b-109">ALL</span></span>  
 <span data-ttu-id="8f55b-110">Spécifie que plusieurs collections doivent être combinées et retournées sous la forme d'une collection unique, y compris les doublons.</span><span class="sxs-lookup"><span data-stu-id="8f55b-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="8f55b-111">Si cet argument n'est pas spécifié, les doublons sont supprimés de la collection des résultats.</span><span class="sxs-lookup"><span data-stu-id="8f55b-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f55b-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8f55b-112">Return Value</span></span>  
 <span data-ttu-id="8f55b-113">Collection du même type que l' `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="8f55b-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f55b-114">Notes</span><span class="sxs-lookup"><span data-stu-id="8f55b-114">Remarks</span></span>  
 <span data-ttu-id="8f55b-115">UNION est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8f55b-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="8f55b-116">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="8f55b-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="8f55b-117">Pour plus d’informations de priorité pour la [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateurs de jeu, consultez [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8f55b-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f55b-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f55b-118">Example</span></span>  
 <span data-ttu-id="8f55b-119">La requête Entity SQL ci-dessous utilise l'opérateur UNION ALL pour combiner les résultats de deux requêtes en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="8f55b-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="8f55b-120">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="8f55b-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8f55b-121">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8f55b-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8f55b-122">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8f55b-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8f55b-123">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="8f55b-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="8f55b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f55b-124">See Also</span></span>  
 [<span data-ttu-id="8f55b-125">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8f55b-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
