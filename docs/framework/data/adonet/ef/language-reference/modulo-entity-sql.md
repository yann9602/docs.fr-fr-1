---
title: "(Modulo) (Entity&#160;SQL) | Microsoft Docs"
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
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# (Modulo) (Entity&#160;SQL)
Retourne le reste d'une expression divisée par une autre.  
  
## Syntaxe  
  
```  
  
dividend  
%  
divisor  
  
```  
  
## Arguments  
 `dividend`  
 Expression numérique à diviser.`dividend` correspond à toute expression valide de l'un des types de données numériques.  
  
 `divisor`  
 Expression numérique par laquelle diviser le dividende.`divisor` correspond à toute expression valide de l'un des types de données numériques.  
  
## Types de résultats  
 Edm.Int32  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur arithmétique % pour retourner le reste d'une expression divisée par une autre. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)