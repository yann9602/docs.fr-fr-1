---
title: "THEN (Entity SQL) | Microsoft Docs"
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
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# THEN (Entity SQL)
Résultat d'une clause WHEN lorsqu'elle prend la valeur `true`.  
  
## Syntaxe  
  
```  
  
WHEN when_expression THEN then_expression  
```  
  
## Arguments  
 `when_expression`  
 Toute expression booléenne valide.  
  
 `then_expression`  
 Toute expression de requête valide qui retourne une collection.  
  
## Notes  
 Si `when_expression` prend la valeur `true`, le résultat est l'expression `then-expression` correspondante. Si aucune des conditions WHEN n'est remplie, `else-expression` est évaluée. Toutefois, en l'absence d'une expression `else-expression`, le résultat est Null.  
  
 Pour obtenir un exemple, consultez [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'expression CASE pour évaluer un ensemble d'expressions `Boolean`. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## Voir aussi  
 [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)   
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)