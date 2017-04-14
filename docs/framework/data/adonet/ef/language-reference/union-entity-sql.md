---
title: "UNION (Entity SQL) | Microsoft Docs"
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
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# UNION (Entity SQL)
Combine les résultats de deux requêtes, ou plus, en une collection unique.  
  
## Syntaxe  
  
```  
  
          expression  
UNION [ ALL ]  
expression  
```  
  
## Arguments  
 `expression`  
 Toute expression de requête valide qui retourne une collection à combiner à la collection. Toutes les expressions doivent être du même type que la valeur `expression` ou d'un type de base commun ou dérivé de celui\-ci.  
  
 UNION  
 Spécifie que plusieurs collections doivent être combinées et retournées sous la forme d'une collection unique.  
  
 ALL  
 Spécifie que plusieurs collections doivent être combinées et retournées sous la forme d'une collection unique, y compris les doublons. Si cet argument n'est pas spécifié, les doublons sont supprimés de la collection des résultats.  
  
## Valeur de retour  
 Collection du même type que l'`expression` ou d'un type de base commun ou dérivé de celui\-ci.  
  
## Notes  
 UNION est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite. Pour obtenir des informations sur la priorité des opérateurs d’ensembles [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consultez [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur UNION ALL pour combiner les résultats de deux requêtes en une collection unique. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)