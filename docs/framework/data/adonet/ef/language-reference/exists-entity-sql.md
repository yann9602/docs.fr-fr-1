---
title: "EXISTS (Entity SQL) | Microsoft Docs"
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
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# EXISTS (Entity SQL)
Détermine si une collection est vide.  
  
## Syntaxe  
  
```  
  
[NOT] EXISTS (expression)  
```  
  
## Arguments  
 `expression`  
 Toute expression valide qui retourne une collection.  
  
 NOT  
 Indique que la valeur du résultat de l'opérateur EXISTS est inversée.  
  
## Valeur de retour  
 `true` si la collection n'est pas vide ; sinon, `false`.  
  
## Notes  
 EXISTS est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite. Pour obtenir des informations sur la priorité des opérateurs d’ensembles [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consultez [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur EXISTS pour déterminer si la collection est vide. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)