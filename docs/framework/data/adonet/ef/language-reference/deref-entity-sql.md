---
title: "DEREF (Entity SQL) | Microsoft Docs"
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
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DEREF (Entity SQL)
Déréférence une valeur de référence et génère le résultat de ce déréférencement.  
  
## Syntaxe  
  
```  
  
SELECT DEREF ( o.expression) from Table as o;  
```  
  
## Arguments  
 `expression`  
 Toute expression de requête valide qui retourne une collection.  
  
## Valeur de retour  
 Valeur de l'entité référencée.  
  
## Notes  
 L'opérateur DEREF déréférence une valeur de référence et génère le résultat de ce déréférencement. Par exemple, si `r` est une référence de type ref\<T\>, `Deref` `(r)` est une expression de type `T` qui génère l’entité référencée par `r`. Si la valeur de référence est null ou non résolue \(autrement dit, la cible de la référence n'existe pas\), le résultat de l'opérateur DEREF est null.  
  
## Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci\-dessous utilise l'opérateur DEREF pour déréférencer une valeur de référence et générer le résultat de ce déréférencement. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Passez à la méthode ExecutePrimitiveTypeQuery la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)   
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)   
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)   
 [Types structurés autorisant la valeur null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)