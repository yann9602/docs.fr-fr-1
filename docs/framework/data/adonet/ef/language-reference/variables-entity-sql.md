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
ms.openlocfilehash: 551b6d6feab6829c9a2f6f2e89e1918acf463411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="variables-entity-sql"></a><span data-ttu-id="95248-102">Variables (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="95248-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="95248-103">Variable</span><span class="sxs-lookup"><span data-stu-id="95248-103">Variable</span></span>  
 <span data-ttu-id="95248-104">Une expression de variable est une référence à une expression nommée dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="95248-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="95248-105">Une référence de variable doit être un [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificateur, tel que défini dans [identificateurs](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="95248-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="95248-106">L'exemple suivant montre l'utilisation d'une variable dans l'expression.</span><span class="sxs-lookup"><span data-stu-id="95248-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="95248-107">Le `c` dans la clause FROM représente la définition de la variable.</span><span class="sxs-lookup"><span data-stu-id="95248-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="95248-108">Le `c` dans la clause SELECT représente la référence à la variable.</span><span class="sxs-lookup"><span data-stu-id="95248-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="95248-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95248-109">See Also</span></span>  
 [<span data-ttu-id="95248-110">Identificateurs</span><span class="sxs-lookup"><span data-stu-id="95248-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="95248-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95248-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="95248-112">Vue d’ensemble de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="95248-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
