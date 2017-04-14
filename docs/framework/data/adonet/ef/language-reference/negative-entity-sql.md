---
title: "- (n&#233;gatif) (Entity SQL) | Microsoft Docs"
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
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# - (n&#233;gatif) (Entity SQL)
Retourne la forme négative de la valeur d'une expression numérique.  
  
## Syntaxe  
  
```  
  
-  
expression  
  
```  
  
## Arguments  
 `expression`  
 Toute expression valide de l'un des types de données numériques.  
  
## Types de résultats  
 Type de données de l'`expression`.  
  
## Notes  
 Si l'`expression` est un type non signé, le type du résultat sera le type signé le plus proche du type de l'`expression`. Par exemple, si l'`expression` est de type Byte, une valeur de type Int16 sera retournée.  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur arithmétique \- pour retourner la forme négative de la valeur d'une expression numérique. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)