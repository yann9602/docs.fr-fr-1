---
title: "ISOF (Entity SQL) | Microsoft Docs"
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
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# ISOF (Entity SQL)
Détermine si le type d'une expression appartient au type spécifié ou à l'un de ses sous\-types.  
  
## Syntaxe  
  
```  
  
expression IS [ NOT ] OF ( [ ONLY ] type)  
```  
  
## Arguments  
 `expression`  
 Toute expression de requête valide pour en déterminer le type.  
  
 NOT  
 Inverse le résultat EDM.Boolean de l'opérateur IS OF.  
  
 ONLY  
 Indique que l'opérateur IS OF ne retourne `true` que si `expression` appartient au type `type` et non à l'un de ses sous\-types.  
  
 `type`  
 Type sur lequel tester `expression`. Le type doit être qualifié par un espace de noms.  
  
## Valeur de retour  
 `true` si `expression` est de type T, qui est soit un type de base, soit un type dérivé de `type` ; null si `expression` a la valeur null au moment de l'exécution ; sinon, `false`.  
  
## Notes  
 Les expressions `expression IS NOT OF (type)` et `expression IS NOT OF (ONLY type)` sont du point de vue syntaxique équivalentes à `NOT (expression IS OF (type))` et `NOT (expression IS OF (ONLY type))`, respectivement.  
  
 Le tableau suivant indique le comportement de l'opérateur `IS OF` sur certains modèles courants et d'autres plus singuliers. Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :  
  
|Modèle|Comportement|  
|------------|------------------|  
|null IS OF \(EntityType\)|Exception|  
|null IS OF \(ComplexType\)|Exception|  
|null IS OF \(RowType\)|Exception|  
|TREAT \(null AS EntityType\) IS OF \(EntityType\)|Retourne DBNull|  
|TREAT \(null AS ComplexType\) IS OF \(ComplexType\)|Exception|  
|TREAT \(null AS RowType\) IS OF \(RowType\)|Exception|  
|EntityType IS OF \(EntityType\)|Retourne true\/false|  
|ComplexType IS OF \(ComplexType\)|Exception|  
|RowType IS OF \(RowType\)|Exception|  
  
## Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci\-dessous utilise l'opérateur IS OF pour déterminer le type d'une expression de requête, puis utilise l'opérateur TREAT pour convertir un objet du type Course en collection d'objets du type OnsiteCourse. Cette requête est basée sur le modèle [School](http://msdn.microsoft.com/fr-fr/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)