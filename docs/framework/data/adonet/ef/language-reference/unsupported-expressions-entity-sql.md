---
title: "Expressions non prises en charge (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Expressions non prises en charge (Entity SQL)
Cette rubrique décrit les expressions [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] qui ne sont pas prises en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Pour plus d'informations, consultez [Différences entre Entity SQL et Transact\-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).  
  
## Prédicats quantifiés  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] autorise les constructions de la forme suivante :  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 Toutefois, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge ces constructions.  Des expressions équivalentes peuvent être écrites dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], comme suit :  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## \*, opérateur  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] prend en charge l'utilisation de l'opérateur \* dans la clause SELECT pour indiquer que toutes les colonnes doivent être projetées.  Cet opérateur n'est pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## Voir aussi  
 [Vue d'ensemble d'Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)   
 [Différences entre Entity SQL et Transact\-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)