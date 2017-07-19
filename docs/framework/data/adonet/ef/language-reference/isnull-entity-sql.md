---
title: "ISNULL (Entity SQL) | Microsoft Docs"
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
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ISNULL (Entity SQL)
Détermine si une expression de requête a la valeur NULL.  
  
## Syntaxe  
  
```  
  
expression IS [ NOT ] NULL  
```  
  
## Arguments  
 `expression`  
 Toute expression de requête valide. Ne peut pas être une collection, posséder des membres de collection ou être un type d'enregistrement avec des propriétés de type collection.  
  
 NOT  
 Inverse le résultat EDM.Boolean de l'opérateur IS NULL.  
  
## Valeur de retour  
 `true` si `expression` retourne la valeur NULL ; sinon, `false`.  
  
## Notes  
 Utilisez `IS NULL` pour déterminer si l'élément d'une jointure externe est NULL :  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Utilisez `IS NULL` pour déterminer si un membre a une valeur réelle :  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Le tableau ci\-dessous montre le comportement de l'opérateur `IS NULL` sur certains modèles. Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :  
  
|Modèle|Comportement|  
|------------|------------------|  
|null IS NULL|Retourne `true`.|  
|TREAT \(null AS EntityType\) IS NULL|Retourne `true`.|  
|TREAT \(null AS ComplexType\) IS NULL|Génère une erreur.|  
|TREAT \(null AS RowType\) IS NULL|Génère une erreur.|  
|EntityType IS NULL|Retourne `true` ou la valeur `false`.|  
|ComplexType IS NULL|Génère une erreur.|  
|RowType IS NULL|Génère une erreur.|  
  
## Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci\-dessous utilise l'opérateur IS NOT NULL pour déterminer si une expression de requête n'a pas la valeur NULL. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)