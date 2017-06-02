---
title: "Comparaisons de valeurs Null | Microsoft Docs"
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
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Comparaisons de valeurs Null
Une valeur `null` dans la source de données indique que la valeur est inconnue.  Dans les requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], vous pouvez vérifier les valeurs Null afin que certains calculs ou certaines comparaisons soient effectués uniquement sur les lignes qui ont des données valides, ou non Null.  Toutefois, la sémantique Null CLR peut différer par rapport à la sémantique Null de la source de données.  La plupart des bases de données utilisent une version de logique à trois valeurs pour gérer les comparaisons de valeurs Null.  Autrement dit, une comparaison avec une valeur Null n'a pas la valeur `true` ou `false` ; elle a la valeur `unknown`.  Il s'agit souvent d'une implémentation de valeurs ANSI Null, mais ce n'est pas toujours le cas.  
  
 Par défaut dans SQL Server, la comparaison Null\-égale\-Null retourne une valeur Null.  Dans l'exemple suivant, les lignes dans lesquelles `ShipDate` a la valeur Null sont exclues du jeu de résultats, et l'instruction [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] retournerait 0 ligne.  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 C'est très différent de la sémantique Null CLR, où la comparaison Null\-égale\-Null retourne true.  
  
 La requête LINQ suivante est exprimée dans le CLR, mais elle est exécutée dans la source de données.  Étant donné que rien ne garantit que la sémantique CLR sera respectée au niveau de la source de données, le comportement attendu est indéterminé.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## Sélecteurs de clé  
 Un *sélecteur de clé* est une fonction utilisée dans les opérateurs de requête standard pour extraire une clé d'un élément.  Dans la fonction du sélecteur de clé, une expression peut être comparée avec une constante.  La sémantique Null CLR est exposée si une expression est comparée à une constante Null ou si deux constantes Null sont comparées.  La sémantique Null du magasin est exposée si deux colonnes contenant des valeurs Null dans la source de données sont comparées.  Les sélecteurs de clé, qui se trouvent dans un grand nombre des opérateurs de requête standard de classement et de regroupement, tels que <xref:System.Linq.Queryable.GroupBy%2A>, sont utilisés pour sélectionner les clés sur lesquelles trier ou regrouper les résultats de la requête.  
  
## Propriété Null sur un objet Null  
 Dans [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], les propriétés d'un objet Null sont Null.  Lorsque vous essayez de référencer une propriété d'un objet Null dans le CLR, vous recevez un objet <xref:System.NullReferenceException>.  Lorsqu'une requête LINQ implique une propriété d'un objet Null, cela peut provoquer un comportement incohérent.  
  
 Par exemple, dans la requête suivante, le cast en `NewProduct` est effectué dans la couche de l'arborescence de commandes, ce qui peut rendre Null la propriété `Introduced`.  Si la base de données a défini des comparaisons de valeurs Null telles que la comparaison <xref:System.DateTime> ait la valeur true, la ligne sera incluse.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## Transmission de collections de valeurs Null aux fonctions d'agrégation  
 Dans [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], lorsque vous passez une collection qui prend en charge `IQueryable` à une fonction d'agrégation, les opérations d'agrégation sont effectuées dans la base de données.  Il peut y avoir des différences entre les résultats d'une requête qui a été effectuée en mémoire et ceux d'une requête qui a été effectuée dans la base de données.  Avec une requête en mémoire, en l'absence de correspondance, la requête retourne zéro.  Dans la base de données, la même requête retourne la valeur `null`.  Si une valeur `null` est transmise à une fonction d'agrégation LINQ, une exception est levée.  Pour accepter les éventuelles valeurs `null`, transtypez les types et les propriétés des types qui reçoivent les résultats de la requête en types Nullable.  
  
## Voir aussi  
 [Expressions dans les requêtes LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)