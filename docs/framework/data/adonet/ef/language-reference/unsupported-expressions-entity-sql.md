---
title: Expressions non prises en charge (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c18c726a962d9a29a3dace1ebd5c2073637bb4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="unsupported-expressions-entity-sql"></a><span data-ttu-id="126ce-102">Expressions non prises en charge (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="126ce-102">Unsupported Expressions (Entity SQL)</span></span>
<span data-ttu-id="126ce-103">Cette rubrique décrit les expressions [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] qui ne sont pas prises en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="126ce-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="126ce-104">Pour plus d’informations, consultez [Entity SQL différences entre Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="126ce-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>  
  
## <a name="quantified-predicates"></a><span data-ttu-id="126ce-105">Prédicats quantifiés</span><span class="sxs-lookup"><span data-stu-id="126ce-105">Quantified Predicates</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="126ce-106"> autorise les constructions de la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="126ce-106"> allows constructs of the following form:</span></span>  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 <span data-ttu-id="126ce-107">Toutefois, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge ces constructions.</span><span class="sxs-lookup"><span data-stu-id="126ce-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="126ce-108">Des expressions équivalentes peuvent être écrites dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], comme suit :</span><span class="sxs-lookup"><span data-stu-id="126ce-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## <a name="-operator"></a><span data-ttu-id="126ce-109">*, opérateur</span><span class="sxs-lookup"><span data-stu-id="126ce-109">* Operator</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="126ce-110"> prend en charge l'utilisation de l'opérateur * dans la clause SELECT pour indiquer que toutes les colonnes doivent être projetées. Cet opérateur n'est pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="126ce-110"> supports the use of the * operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126ce-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="126ce-111">See Also</span></span>  
 [<span data-ttu-id="126ce-112">Vue d’ensemble de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="126ce-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="126ce-113">Différences entre Entity SQL à partir de Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="126ce-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
