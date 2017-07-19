---
title: "&lt; (Inf&#233;rieur &#224;) (Entity SQL) | Microsoft Docs"
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
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# &lt; (Inf&#233;rieur &#224;) (Entity SQL)
Compare deux expressions pour déterminer si la valeur de l'expression de gauche est inférieure à celle de l'expression de droite.  
  
## Syntaxe  
  
```  
  
expression  
<  
expression  
  
```  
  
## Arguments  
 `expression`  
 Toute expression valide. Les deux expressions doivent posséder des types de données implicitement convertibles.  
  
## Types de résultats  
 `true` si la valeur de l'expression de gauche est inférieure à celle de l'expression de droite ; sinon, `false`.  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur de comparaison \< pour comparer deux expressions afin de déterminer si la valeur de l'expression de gauche est inférieure à celle de l'expression de droite. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)