---
title: "- (soustraction) (Entity SQL) | Microsoft Docs"
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
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# - (soustraction) (Entity SQL)
Soustrait deux nombres.  
  
## Syntaxe  
  
```  
  
expression  
-  
expression  
  
```  
  
## Arguments  
 `expression`  
 Toute expression valide de l'un des types de données numériques.  
  
## Types de résultats  
 Type de données qui résulte de la promotion de type implicite de deux arguments. Pour plus d’informations sur la promotion de type implicite, consultez [système de type](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur arithmétique \- pour soustraire deux nombres. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)