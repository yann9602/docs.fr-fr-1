---
title: "LIMIT (Entity SQL) | Microsoft Docs"
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
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# LIMIT (Entity SQL)
Une pagination physique peut être effectuée par le biais de la sous\-clause LIMIT de la clause ORDER BY. La sous\-clause LIMIT ne peut pas être utilisée sans la clause ORDER BY.  
  
## Syntaxe  
  
```  
  
[ LIMIT n ]  
```  
  
## Arguments  
 `n`  
 Nombre d'éléments qui seront sélectionnés.  
  
 Si une sous\-clause d'expression LIMIT est présente dans une clause ORDER BY, la requête sera triée en fonction de la spécification de classement et le nombre de lignes obtenu sera limité par l'expression LIMIT. Par exemple, LIMIT 5 limitera le jeu de résultats à 5 instances ou lignes. LIMIT est d'un point de vue fonctionnel équivalent à TOP, sauf que LIMIT a besoin de la présence de la clause ORDER BY. SKIP et LIMIT peuvent être utilisés indépendamment avec la clause ORDER BY.  
  
> [!NOTE]
>  Une requête Entity SQL est considérée comme non valide si le modificateur TOP et la sous\-clause SKIP se trouvent dans une même expression de requête. La requête doit être réécrite en remplaçant l'expression TOP par l'expression LIMIT.  
  
## Exemple  
 La requête Entity SQL suivante utilise l'opérateur ORDER BY avec LIMIT pour spécifier l'ordre de classement employé sur les objets retournés dans une instruction SELECT. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## Voir aussi  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)   
 [Procédure : pagination dans les résultats d’une requête](http://msdn.microsoft.com/fr-fr/ffc0f920-e7de-42e0-9b12-ef356421d030)   
 [Pagination](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)   
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)