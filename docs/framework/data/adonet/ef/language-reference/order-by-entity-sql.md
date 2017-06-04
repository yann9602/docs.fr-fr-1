---
title: "ORDER BY (Entity SQL) | Microsoft Docs"
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
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ORDER BY (Entity SQL)
Spécifie l'ordre de classement utilisé sur les objets retournés dans une instruction SELECT.  
  
## Syntaxe  
  
```  
  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## Arguments  
 `order_by_expression`  
 Toute expression de requête valide qui spécifie une propriété sur laquelle doit porter le tri. Vous pouvez spécifier plusieurs expressions de classement. L'ordre des expressions de classement dans la clause ORDER BY détermine l'organisation de l'ensemble de résultats trié.  
  
 COLLATE {collation\_name}  
 Indique que l'opération ORDER BY doit être effectuée en fonction du classement spécifié dans `collation_name`. COLLATE ne peut s'appliquer qu'aux expressions de chaîne.  
  
 ASC  
 Indique que les valeurs de la propriété spécifiée doivent être triées dans l'ordre croissant, de la plus petite à la plus grande. Il s'agit de la valeur par défaut.  
  
 DESC  
 Indique que les valeurs de la propriété spécifiée doivent être triées dans l'ordre décroissant, de la plus grande à la plus petite.  
  
 LIMIT `n`  
 Seuls les `n` premiers éléments sont sélectionnés.  
  
 SKIP `n`  
 Ignore les `n` premiers éléments.  
  
## Notes  
 La clause ORDER BY est logiquement appliquée au résultat de la clause SELECT. La clause ORDER BY peut faire référence aux éléments de la liste de sélection avec leurs alias. La clause ORDER BY peut également faire référence à d'autres variables qui se trouvent actuellement dans l'étendue. Toutefois, si la clause SELECT a été spécifiée avec un modificateur DISTINCT, la clause ORDER BY ne peut faire référence qu'à des alias de la clause SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Chaque expression contenue dans la clause ORDER BY doit correspondre à un type pouvant être comparé en inégalité \(inférieur à ou supérieur à, etc.\). Ces types sont généralement des primitives scalaires telles que des nombres, des chaînes et des dates. Les RowTypes de type comparable peuvent également être comparés sur le plan de l'ordre de classement.  
  
 Si votre code effectue une itération sur un ensemble ordonné autre qu'une projection de niveau supérieur, il n'est pas garanti que le résultat conservera son ordre de classement.  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Pour une opération UNION, UNION ALL, EXCEPT ou INTERSECT triée, utilisez le modèle suivant :  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## Mots clés restreints  
 Les mots clés suivants doivent être mis entre guillemets lorsqu'ils sont utilisés dans une clause `ORDER BY` :  
  
-   CROSS  
  
-   FULL  
  
-   KEY  
  
-   LEFT  
  
-   ORDER  
  
-   OUTER  
  
-   RIGHT  
  
-   ROW  
  
-   VALUE  
  
## Ordre de tri des requêtes imbriquées  
 Dans Entity Framework, une expression imbriquée peut être placée n'importe où dans la requête ; l'ordre d'une requête imbriquée n'est pas conservé.  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci\-dessous utilise l'opérateur ORDER BY pour spécifier l'ordre de tri employé sur les objets retournés dans une instruction SELECT. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## Voir aussi  
 [Expressions de requête](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)   
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)   
 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)   
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)