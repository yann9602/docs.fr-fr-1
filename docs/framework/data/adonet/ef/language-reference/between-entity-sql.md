---
title: "BETWEEN (Entity SQL) | Microsoft Docs"
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
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# BETWEEN (Entity SQL)
Détermine si une expression a pour résultat une valeur contenue dans une plage spécifiée. L'expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN a la même fonction que l'expression Transact\-SQL BETWEEN.  
  
## Syntaxe  
  
```  
  
expression [ NOT ] BETWEEN begin_expression AND end_expression  
```  
  
## Arguments  
 `expression`  
 Toute expression valide à tester dans la plage définie par `begin_expression` et `end_expression`.`expression` doit être du même type qu'`begin_expression` et `end_expression`.  
  
 `begin_expression`  
 Toute expression valide.`begin_expression` doit être du même type qu'`expression` et `end_expression`.`begin_expression` doit être inférieur à `end_expression` ou la valeur de retour sera niée.  
  
 `end_expression`  
 Toute expression valide.`end_expression` doit être du même type qu'`expression` et `begin_expression`.  
  
 NOT  
 Indique que le résultat de BETWEEN est inversé.  
  
 AND  
 Espace réservé qui indique que `expression` doit se trouver dans la plage définie par `begin_expression` et `end_expression`.  
  
## Valeur de retour  
 `true` si `expression` est entre la plage indiquée par `begin_expression` et `end_expression` ; sinon, `false`. La valeur `null` est retournée si `expression` a la valeur `null` ou si `begin_expression` ou `end_expression` a la valeur `null`.  
  
## Notes  
 Pour spécifier une plage exclusive, utilisez les opérateurs « supérieur à » \(\>\) et « inférieur à » \(\<\) à la place de BETWEEN.  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur BETWEEN pour déterminer si une expression génère une valeur située dans une plage spécifiée. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)