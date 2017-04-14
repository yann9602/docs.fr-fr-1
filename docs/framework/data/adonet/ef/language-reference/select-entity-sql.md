---
title: "SELECT (Entity SQL) | Microsoft Docs"
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
  - "ESQL"
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# SELECT (Entity SQL)
Indique les éléments retournés par une requête.  
  
## Syntaxe  
  
```  
  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## Arguments  
 ALL  
 Indique que les doublons peuvent apparaître dans l'ensemble de résultats. ALL est la valeur par défaut.  
  
 DISTINCT  
 Indique que seuls les résultats uniques peuvent apparaître dans l'ensemble de résultats.  
  
 VALUE  
 Autorise la spécification d'un seul élément et n'ajoute pas de wrapper de ligne.  
  
 `topSubclause`  
 Toute expression valide indiquant le nombre de premiers résultats à retourner de la requête, sous la forme `top (``expr``)`.  
  
 Le paramètre LIMIT de l’opérateur [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) permet également de sélectionner les n premiers éléments dans le jeu de résultats.  
  
 `aliasedExpr`  
 Expression sous la forme :  
  
 `expr` comme `identifier` &#124; `expr`  
  
 `expr`  
 Littéral ou expression.  
  
## Notes  
 La clause SELECT est évaluée après les clauses [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) et [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md). La clause SELECT ne peut faire référence qu'aux éléments qui se trouvent actuellement dans l'étendue \(de la clause FROM ou d'étendues externes\). Si une clause GROUP BY a été spécifiée, la clause SELECT ne peut faire référence qu'aux alias des clés GROUP BY. Le référencement des éléments de la clause FROM n'est autorisé que dans les fonctions d'agrégation.  
  
 La liste constituée d'une ou plusieurs expressions de requête figurant après le mot clé SELECT est appelée « liste de sélection » ou, de manière plus formelle, « projection ». La forme de projection la plus courante est une expression de requête unique. Si vous sélectionnez un membre `member1` dans une collection  `collection1`, vous générez une nouvelle collection constituée de toutes les valeurs `member1` pour chaque objet de `collection1`, comme l'illustre l'exemple suivant.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Par exemple, si `customers` est une collection de type `Customer` possédant une propriété `Name` de type `string`, le fait de sélectionner `Name` dans `customers` génèrera une collection de chaînes, comme l'illustre l'exemple suivant.  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 Il est également possible d'utiliser la syntaxe JOIN \(FULL, INNER, LEFT, OUTER, ON et RIGHT\). ON est requis pour les jointures internes et n'est pas autorisé pour les jointures croisées.  
  
## Clauses « row select » et « value select »  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge deux variantes de la clause SELECT. La première variante, « row select », est identifiée par le mot clé SELECT et peut être utilisée pour spécifier une ou plusieurs valeurs devant être projetées. Étant donné qu'un wrapper de ligne est implicitement ajouté de part et d'autre des valeurs retournées, le résultat de l'expression de requête est toujours un multiensemble de lignes.  
  
 Chaque expression de requête figurant dans une clause « row select » doit spécifier un alias. Si aucun alias n'est spécifié, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] essaie d'en générer un en utilisant les règles de génération d'alias.  
  
 L'autre variante de la clause SELECT, « value select », est identifiée par le mot clé SELECT VALUE. Elle autorise la spécification d'une seule valeur et n'ajoute pas de wrapper de ligne.  
  
 Une clause « row select » peut toujours être exprimée en termes de sélection de valeur \(SELECT VALUE\), comme l'illustre l'exemple suivant.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## Modificateurs All et Distinct  
 Les deux variantes de la clause SELECT d'[!INCLUDE[esql](../../../../../../includes/esql-md.md)] permettent de spécifier un modificateur ALL ou DISTINCT. Si le modificateur DISTINCT est spécifié, les doublons sont éliminés de la collection créée par l'expression de requête \(jusqu'à la clause SELECT elle\-même incluse\). Si le modificateur ALL est spécifié, aucune élimination de doublons n'est réalisée ; ALL est spécifié par défaut.  
  
## Différences par rapport à Transact\-SQL  
 Contrairement à Transact\-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge l'utilisation de l'argument \* dans la clause SELECT.  En revanche, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] autorise les requêtes pour projeter des enregistrements entiers en faisant référence aux alias de collection de la clause FROM, comme l'illustre l'exemple suivant.  
  
```  
SELECT * FROM T1, T2  
```  
  
 L'expression de requête [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] précédente est exprimée dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de la façon suivante :  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur SELECT pour spécifier les éléments qu'une requête doit retourner. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## Voir aussi  
 [Expressions de requête](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)   
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)