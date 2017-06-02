---
title: "Pagination (Entity SQL) | Microsoft Docs"
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
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Pagination (Entity SQL)
La pagination physique peut être effectuée à l'aide des sous\-clauses [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) et [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) de la clause [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  Pour effectuer une pagination physique de façon déterministe, vous devez utiliser SKIP et LIMIT.  Si vous voulez uniquement restreindre le nombre de lignes dans le résultat d'une façon non déterministe, vous devez utiliser [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  TOP et SKIP\/LIMIT s'excluent mutuellement.  
  
## Vue d'ensemble de TOP  
 La clause SELECT peut avoir une sous\-clause TOP facultative après le modificateur ALL\/DISTINCT facultatif.  La sous\-clause TOP spécifie que seul le premier ensemble de lignes sera retourné à partir du résultat de la requête.  Pour plus d'informations, voir [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  
  
## Vue d'ensemble de SKIP et de LIMIT  
 SKIP et LIMIT qui font partie de la clause ORDER BY.  Si une sous\-clause d'expression SKIP est présente dans une clause ORDER BY, les résultats seront triés en fonction de la spécification de classement et le jeu de résultats inclura une ou plusieurs lignes en commençant à la prochaine ligne immédiatement après l'expression SKIP.  Par exemple, SKIP 5 ignore les cinq premières lignes et retourne la sixième ligne et les suivantes.  Si une sous\-clause d'expression LIMIT est présente dans une clause ORDER BY, la requête sera triée en fonction de la spécification de classement et le nombre de lignes obtenu sera limité par l'expression LIMIT.  Par exemple, LIMIT 5 limitera le jeu de résultats à cinq instances ou lignes.  SKIP et LIMIT ne doivent pas nécessairement être utilisées ensemble ; vous pouvez utiliser uniquement SKIP ou uniquement LIMIT avec la clause ORDER BY.  Pour plus d'informations, consultez les rubriques suivantes :  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Vue d'ensemble d'Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)   
 [How to: Page Through Query Results](http://msdn.microsoft.com/fr-fr/ffc0f920-e7de-42e0-9b12-ef356421d030)