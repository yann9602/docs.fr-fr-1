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
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
La clause WHERE est appliquée directement après le [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Type booléen.  
  
## <a name="remarks"></a>Notes  
 La sémantique de la clause WHERE est identique à celle décrite pour [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Elle restreint le nombre d'objets générés par l'expression de requête en limitant les éléments des collections sources à ceux qui répondent à la condition.  
  
```  
select c from cs as c where e  
```  
  
 L'expression `e` doit être de type booléen.  
  
 La clause WHERE est appliquée directement après la clause FROM et avant tout regroupement, classement ou projection éventuel. Tous les noms d'éléments définis dans la clause FROM sont visibles pour l'expression de la clause WHERE.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Expressions de requête](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
