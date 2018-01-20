---
title: Pagination (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: dfbd282eed19fdfa81a1dda5d06d41a80386feaa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="paging-entity-sql"></a><span data-ttu-id="61b9e-102">Pagination (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="61b9e-102">Paging (Entity SQL)</span></span>
<span data-ttu-id="61b9e-103">Pagination physique peut être effectuée à l’aide de la [ignorer](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) et [limite](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sous-clauses dans le [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span><span class="sxs-lookup"><span data-stu-id="61b9e-103">Physical paging can be performed by using the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="61b9e-104">Pour effectuer une pagination physique de façon déterministe, vous devez utiliser SKIP et LIMIT.</span><span class="sxs-lookup"><span data-stu-id="61b9e-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="61b9e-105">Si vous voulez uniquement restreindre le nombre de lignes dans le résultat d’une manière non déterministe, vous devez utiliser [haut](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="61b9e-105">If you only want to restrict the number of rows in the result in a non-determinsitic way, you should use [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span> <span data-ttu-id="61b9e-106">TOP et SKIP/LIMIT s'excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="61b9e-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="61b9e-107">Vue d'ensemble de TOP</span><span class="sxs-lookup"><span data-stu-id="61b9e-107">TOP Overview</span></span>  
 <span data-ttu-id="61b9e-108">La clause SELECT peut avoir une sous-clause TOP facultative après le modificateur ALL/DISTINCT facultatif.</span><span class="sxs-lookup"><span data-stu-id="61b9e-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="61b9e-109">La sous-clause TOP spécifie que seul le premier ensemble de lignes sera retourné à partir du résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="61b9e-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="61b9e-110">Pour plus d’informations, consultez [haut](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="61b9e-110">For more information, see [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="61b9e-111">Vue d'ensemble de SKIP et de LIMIT</span><span class="sxs-lookup"><span data-stu-id="61b9e-111">SKIP And LIMIT Overview</span></span>  
 <span data-ttu-id="61b9e-112">SKIP et LIMIT qui font partie de la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="61b9e-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="61b9e-113">Si une sous-clause d'expression SKIP est présente dans une clause ORDER BY, les résultats seront triés en fonction de la spécification de classement et le jeu de résultats inclura une ou plusieurs lignes en commençant à la prochaine ligne immédiatement après l'expression SKIP.</span><span class="sxs-lookup"><span data-stu-id="61b9e-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="61b9e-114">Par exemple, SKIP 5 ignore les cinq premières lignes et retourne la sixième ligne et les suivantes.</span><span class="sxs-lookup"><span data-stu-id="61b9e-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="61b9e-115">Si une sous-clause d'expression LIMIT est présente dans une clause ORDER BY, la requête sera triée en fonction de la spécification de classement et le nombre de lignes obtenu sera limité par l'expression LIMIT.</span><span class="sxs-lookup"><span data-stu-id="61b9e-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="61b9e-116">Par exemple, LIMIT 5 limitera le jeu de résultats à cinq instances ou lignes.</span><span class="sxs-lookup"><span data-stu-id="61b9e-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="61b9e-117">SKIP et LIMIT ne doivent pas nécessairement être utilisées ensemble ; vous pouvez utiliser uniquement SKIP ou uniquement LIMIT avec la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="61b9e-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="61b9e-118">Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="61b9e-118">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="61b9e-119">SKIP</span><span class="sxs-lookup"><span data-stu-id="61b9e-119">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [<span data-ttu-id="61b9e-120">LIMIT</span><span class="sxs-lookup"><span data-stu-id="61b9e-120">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [<span data-ttu-id="61b9e-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="61b9e-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="61b9e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61b9e-122">See Also</span></span>  
 [<span data-ttu-id="61b9e-123">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="61b9e-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="61b9e-124">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="61b9e-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="61b9e-125">Comment : résultats de la Page via la requête</span><span class="sxs-lookup"><span data-stu-id="61b9e-125">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
