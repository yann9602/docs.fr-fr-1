---
title: "FLATTEN (Entity SQL) | Microsoft Docs"
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
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# FLATTEN (Entity SQL)
Convertit une collection de collections en collection plane. La nouvelle collection contient les mêmes éléments que l'ancienne, mais sans structure imbriquée.  
  
## Syntaxe  
  
```  
  
FLATTEN ( collection )  
```  
  
## Arguments  
 `collection`  
 Expression valide qui retourne une collection de collections de valeurs à aplanir en une seule.  
  
## Notes  
 `FLATTEN` est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite. Pour obtenir des informations sur la priorité des opérateurs d’ensembles [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consultez [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur `FLATTEN` pour convertir une collection de collections en collection plane. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)