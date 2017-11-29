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
# <a name="unsupported-expressions-entity-sql"></a>Expressions non prises en charge (Entity SQL)
Cette rubrique décrit les expressions [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] qui ne sont pas prises en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Pour plus d’informations, consultez [Entity SQL différences entre Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).  
  
## <a name="quantified-predicates"></a>Prédicats quantifiés  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] autorise les constructions de la forme suivante :  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 Toutefois, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge ces constructions. Des expressions équivalentes peuvent être écrites dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], comme suit :  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## <a name="-operator"></a>*, opérateur  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] prend en charge l'utilisation de l'opérateur * dans la clause SELECT pour indiquer que toutes les colonnes doivent être projetées. Cet opérateur n'est pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Différences entre Entity SQL à partir de Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
