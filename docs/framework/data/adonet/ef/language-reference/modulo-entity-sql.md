---
title: "(Modulo) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cff0e4eaadf601b7a90f3caa0ecd9cf2f48feab0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="eb16c-102">(Modulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="eb16c-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="eb16c-103">Retourne le reste d'une expression divisée par une autre.</span><span class="sxs-lookup"><span data-stu-id="eb16c-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb16c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb16c-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb16c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="eb16c-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="eb16c-106">Expression numérique à diviser.</span><span class="sxs-lookup"><span data-stu-id="eb16c-106">The numeric expression to divide.</span></span> <span data-ttu-id="eb16c-107">`dividend` correspond à toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="eb16c-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="eb16c-108">Expression numérique par laquelle diviser le dividende.</span><span class="sxs-lookup"><span data-stu-id="eb16c-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="eb16c-109">`divisor` correspond à toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="eb16c-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="eb16c-110">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="eb16c-110">Result Types</span></span>  
 <span data-ttu-id="eb16c-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="eb16c-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb16c-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb16c-112">Example</span></span>  
 <span data-ttu-id="eb16c-113">La requête Entity SQL ci-dessous utilise l'opérateur arithmétique % pour retourner le reste d'une expression divisée par une autre.</span><span class="sxs-lookup"><span data-stu-id="eb16c-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="eb16c-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="eb16c-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="eb16c-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="eb16c-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="eb16c-116">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="eb16c-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="eb16c-117">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="eb16c-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="eb16c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb16c-118">See Also</span></span>  
 [<span data-ttu-id="eb16c-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eb16c-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
