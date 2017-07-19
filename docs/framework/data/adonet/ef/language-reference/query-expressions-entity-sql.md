---
title: "Expressions de requ&#234;te (Entity SQL) | Microsoft Docs"
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
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Expressions de requ&#234;te (Entity SQL)
Une expression de requête combine un grand nombre d'opérateurs de requête différents dans une syntaxe unique.  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit différents types d'expressions, dont notamment : des [littéraux](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), des [paramètres](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [variables](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), des opérateurs, des [fonctions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), des opérateurs Set, et ainsi de suite.  Pour plus d'informations, consultez [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## Clauses  
 Une expression de requête est constituée d'une série de clauses qui appliquent des opérations successives à une collection d'objets.  Elles sont basées sur les mêmes clauses contenues dans une instruction SQL SELECT standard : [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) et [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## Portée  
 Les noms définis dans la clause FROM sont introduits dans l'étendue FROM dans l'ordre de leur apparition, de gauche à droite.  Dans la liste JOIN, les expressions peuvent faire référence aux noms définis précédemment dans la liste.  Les propriétés publiques des éléments identifiés dans la clause FROM ne sont pas ajoutées à l'étendue FROM : elles doivent toujours être référencées par le biais du nom qualifié par un alias.  Normalement, toutes les parties de l'expression select sont considérées comme faisant partie de l'étendue FROM.  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)