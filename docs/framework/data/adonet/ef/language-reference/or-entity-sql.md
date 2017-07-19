---
title: "|| (OR) (Entity SQL) | Microsoft Docs"
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
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# || (OR) (Entity SQL)
Combine deux expressions `Boolean`.  
  
## Syntaxe  
  
```  
  
          boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## Arguments  
 `boolean_expression`  
 Toute expression valide qui retourne une valeur `Boolean`.  
  
## Valeur de retour  
 `true` si l'une des conditions a la valeur `true` ; sinon, `false`.  
  
## Notes  
 OR est un opérateur logique [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Il est utilisé pour combiner deux conditions. Lorsque vous utilisez plusieurs opérateurs logiques dans une instruction, les opérateurs OR sont évalués après les opérateurs AND. L'utilisation de parenthèses permet toutefois de modifier l'ordre de traitement.  
  
 Les doubles barres verticales \(&#124;&#124;\) ont la même fonctionnalité que l'opérateur OR.  
  
 Le tableau ci\-dessous indique les valeurs d'entrée et les types de retour possibles.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur OR pour combiner deux expressions `Boolean`. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)