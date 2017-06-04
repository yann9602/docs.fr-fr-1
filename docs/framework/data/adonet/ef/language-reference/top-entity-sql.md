---
title: "TOP (Entity SQL) | Microsoft Docs"
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
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# TOP (Entity SQL)
La clause SELECT peut avoir une sous\-clause TOP facultative après le modificateur ALL\/DISTINCT facultatif. La sous\-clause TOP spécifie que seul le premier ensemble de lignes sera retourné à partir du résultat de la requête.  
  
## Syntaxe  
  
```  
  
[ TOP (n) ]  
```  
  
## Arguments  
 `n`  
 Expression numérique qui précise le nombre de lignes à retourner.`n` peut être un littéral numérique unique ou un paramètre unique.  
  
## Notes  
 L'expression TOP doit être un littéral numérique unique ou un paramètre unique. Si un littéral constant est utilisé, le type de littéral doit implicitement pouvoir être promu en Edm.Int64 \(octet, int16, int32 ou int64 ou tout type de fournisseur correspondant à un type qui peut être promu en Edm.Int64\) et sa valeur doit être supérieure ou égale au zéro. Dans le cas contraire, une exception est levée. Si un paramètre est utilisé comme expression, le type du paramètre doit aussi pouvoir être implicitement promu en Edm.Int64, mais la valeur réelle du paramètre ne pourra pas être validée au moment de la compilation, car les valeurs de paramètres sont liées tardivement.  
  
 L'exemple suivant est une expression TOP constante :  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 L'exemple suivant est une expression TOP paramétrée :  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 TOP n'est pas déterministe, à moins que la requête soit triée. Si vous avez besoin d'un résultat déterministe, utilisez les sous\-clauses [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) et [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dans la clause [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md). TOP et SKIP\/LIMIT s'excluent mutuellement.  
  
## Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivante utilise TOP pour spécifier la ligne supérieure à retourner à partir du résultat de la requête. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## Voir aussi  
 [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)   
 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)   
 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)   
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)   
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)