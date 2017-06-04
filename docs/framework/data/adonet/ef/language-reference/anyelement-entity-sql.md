---
title: "ANYELEMENT (Entity SQL) | Microsoft Docs"
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
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ANYELEMENT (Entity SQL)
Extrait un élément d'une collection à valeurs multiples.  
  
## Syntaxe  
  
```  
  
ANYELEMENT (expression)  
```  
  
## Arguments  
 `expression`  
 Toute expression de requête valide qui retourne une collection dont extraire un élément.  
  
## Valeur de retour  
 Élément unique de la collection ou élément arbitraire si la collection en comporte plusieurs ; si la collection est vide, retourne `null`. Si```collection```est une collection de type `Collection<T>`,  `ANYELEMENT(collection)` est une expression valide qui produit une instance de type `T`.  
  
## Notes  
 ANYELEMENT extrait un élément arbitraire d'une collection à valeurs multiples. L'exemple ci\-dessous tente d'extraire un élément singleton du jeu `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci\-dessous utilise l'opérateur ANYELEMENT pour extraire un élément d'une collection à valeurs multiples. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Types structurés autorisant la valeur null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)