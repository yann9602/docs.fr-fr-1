---
title: Variables (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fff24c4572fab483c701a93167c0f229d5111d61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="variables-entity-sql"></a><span data-ttu-id="a569d-102">Variables (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a569d-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="a569d-103">Variable</span><span class="sxs-lookup"><span data-stu-id="a569d-103">Variable</span></span>  
 <span data-ttu-id="a569d-104">Une expression de variable est une référence à une expression nommée dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="a569d-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="a569d-105">Une référence de variable doit être un [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificateur, tel que défini dans [identificateurs](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a569d-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="a569d-106">L'exemple suivant montre l'utilisation d'une variable dans l'expression.</span><span class="sxs-lookup"><span data-stu-id="a569d-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="a569d-107">Le `c` dans la clause FROM représente la définition de la variable.</span><span class="sxs-lookup"><span data-stu-id="a569d-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="a569d-108">Le `c` dans la clause SELECT représente la référence à la variable.</span><span class="sxs-lookup"><span data-stu-id="a569d-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="a569d-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a569d-109">See Also</span></span>  
 [<span data-ttu-id="a569d-110">Identificateurs</span><span class="sxs-lookup"><span data-stu-id="a569d-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="a569d-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a569d-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="a569d-112">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a569d-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
