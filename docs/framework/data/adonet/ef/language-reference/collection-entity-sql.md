---
title: "COLLECTION (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# COLLECTION (Entity SQL)
Le mot clé COLLECTION est utilisé uniquement dans la définition d'une fonction incluse. Les fonctions de collection sont des fonctions qui fonctionnent sur une collection de valeurs et produisent une sortie scalaire.  
  
## Syntaxe  
  
```  
  
COLLECTION(type_definition)   
```  
  
## Arguments  
 `type_definition`  
 Expression qui retourne une collection de types, lignes ou références pris en charge.  
  
## Notes  
 Pour plus d’informations sur le mot clé COLLECTION, consultez [Définitions de types](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).  
  
## Exemple  
 L'exemple suivant montre comment utiliser le mot clé COLLECTION pour déclarer une collection de décimales en tant qu'argument pour une fonction de requête incluse.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)