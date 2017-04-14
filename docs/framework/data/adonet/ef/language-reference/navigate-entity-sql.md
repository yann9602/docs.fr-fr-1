---
title: "NAVIGATE (Entity SQL) | Microsoft Docs"
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
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# NAVIGATE (Entity SQL)
Parcourt la relation établie entre des entités.  
  
## Syntaxe  
  
```  
  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## Arguments  
 `instance-expresssion`  
 Instance d'une entité.  
  
 `relationship-type`  
 Nom du type de relation, à partir du fichier CSDL \(Conceptual Schema Definition Language\). Le `relationship-type` est nommé \<espace de noms\>.\<nom du type de relation\>.  
  
 `to`  
 Fin de la relation.  
  
 `from`  
 Début de la relation.  
  
## Valeur de retour  
 Si la cardinalité de la terminaison To est 1, la valeur retournée est `Ref<T>`. Si la cardinalité de la terminaison To est n, la valeur retournée est `Collection<Ref<T>>`.  
  
## Notes  
 Les relations sont des constructions de première classe dans le modèle EDM \([!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)]\). Elles peuvent être établies entre plusieurs types d'entités et les utilisateurs peuvent les parcourir d'une terminaison \(entité\) à l'autre.`from` et `to` sont facultatifs à la condition qu'il n'existe aucune ambiguïté au niveau de la résolution des noms dans la relation.  
  
 NAVIGATE est valide dans l'espace O et C.  
  
 Une construction de navigation se présente généralement sous la forme suivante :  
  
 navigate\(`instance-expresssion`, `relationship-type`, \[ `to-end` \[, `from-end` \] \] \)  
  
 Par exemple :  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 Où OrderCustomer est le `relationship`, et Client et Order sont les terminaisons `to-end` \(customer\) et `from-end` \(order\) de la relation. Si OrderCustomer était une relation de type n:1, le type de résultat de l'expression de navigation serait alors Ref\<Customer\>.  
  
 Voici la même expression sous une forme plus simple :  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 De même, dans une requête de la forme suivante, l'expression de navigation produirait le résultat Collection\<Ref\<Order\>\>.  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 L'expression d'instance doit être un type entity\/ref.  
  
## Exemple  
 La requête Entity SQL suivante utilise l'opérateur NAVIGATE pour parcourir la relation établie entre les types d'entités Address et SalesOrderHeader. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [How to: Navigate Relationships with Navigate Operator](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)