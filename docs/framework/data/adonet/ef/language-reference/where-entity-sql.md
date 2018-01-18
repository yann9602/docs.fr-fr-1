---
title: WHERE (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 11687b1218c61acde7a68bb8fc112e287e5e1c38
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="where-entity-sql"></a><span data-ttu-id="cf29d-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cf29d-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="cf29d-103">La clause WHERE est appliquée directement après le [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span><span class="sxs-lookup"><span data-stu-id="cf29d-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf29d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf29d-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="cf29d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cf29d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="cf29d-106">Type booléen.</span><span class="sxs-lookup"><span data-stu-id="cf29d-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf29d-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cf29d-107">Remarks</span></span>  
 <span data-ttu-id="cf29d-108">La sémantique de la clause WHERE est identique à celle décrite pour [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf29d-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cf29d-109">Elle restreint le nombre d'objets générés par l'expression de requête en limitant les éléments des collections sources à ceux qui répondent à la condition.</span><span class="sxs-lookup"><span data-stu-id="cf29d-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="cf29d-110">L'expression `e` doit être de type booléen.</span><span class="sxs-lookup"><span data-stu-id="cf29d-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="cf29d-111">La clause WHERE est appliquée directement après la clause FROM et avant tout regroupement, classement ou projection éventuel.</span><span class="sxs-lookup"><span data-stu-id="cf29d-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="cf29d-112">Tous les noms d'éléments définis dans la clause FROM sont visibles pour l'expression de la clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="cf29d-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf29d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf29d-113">See Also</span></span>  
 [<span data-ttu-id="cf29d-114">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cf29d-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="cf29d-115">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="cf29d-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
