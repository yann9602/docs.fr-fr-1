---
title: "Requ&#234;tes dans LINQ to Entities | Microsoft Docs"
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
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Requ&#234;tes dans LINQ to Entities
Une requête est une expression qui récupère des données d'une source de données.  En général, les requêtes sont exprimées dans un langage de requête spécialisé, tel que SQL pour les bases de données relationnelles et Xquery pour XML.  Par conséquent, les développeurs ont dû apprendre un nouveau langage de requête pour chaque type de source de données ou format de données qu'ils interrogent.  LINQ \(Language\-Integrated Query\) propose un modèle cohérent plus simple qui permet d'utiliser des données de types de sources et de formats divers.  Dans une requête LINQ, vous travaillez toujours avec des objets de programmation.  
  
 Une opération de requête LINQ se compose de trois actions : obtenir la ou les sources de données, créer la requête, puis exécuter cette dernière.  
  
 Les sources de données qui implémentent l'interface générique <xref:System.Collections.Generic.IEnumerable%601> ou l'interface générique <xref:System.Linq.IQueryable%601> peuvent être interrogées via LINQ.  Les instances de la classe générique <xref:System.Data.Objects.ObjectQuery%601>, laquelle implémente l'interface générique <xref:System.Linq.IQueryable%601>, servent de source de données pour les requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  La classe générique <xref:System.Data.Objects.ObjectQuery%601> représente une requête qui retourne une collection de zéro, un ou plusieurs objets typés.  Vous pouvez également laisser le compilateur déduire le type d'une entité en utilisant le mot clé C\# `var` \(Dim en Visual Basic\).  
  
 Dans la requête, vous spécifiez exactement les informations que vous voulez récupérer à partir de la source de données.  Une requête peut également spécifier la manière dont ces informations doivent être triées, regroupées et mises en forme avant d'être retournées.  Dans LINQ, une requête est stockée dans une variable.  Si la requête retourne une séquence de valeurs, la variable de requête doit elle\-même être de type requêtable.  Cette variable de requête n'effectue aucune action et ne retourne aucune donnée ; elle stocke uniquement les informations de requête.  Une fois que vous avez créé une requête, vous devez l'exécuter pour extraire des données.  
  
## Syntaxe de requête  
 Les requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] peuvent être composées dans deux syntaxes différentes : la syntaxe d'expression de requête et la syntaxe de requête fondée sur une méthode.  La syntaxe d'expression de requête est une caractéristique nouvelle dans C\# 3.0 et Visual Basic 9.0. Elle est constituée d'un ensemble de clauses écrites dans une syntaxe déclarative similaire à Transact\-SQL ou XQuery.  Toutefois, le Common Language Runtime \(CLR\) du [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ne peut pas lire la syntaxe d'expression de requête proprement dite.  Par conséquent, au moment de la compilation, les expressions de requête sont traduites en appels de méthodes pour que le CLR puisse les comprendre.  Ces méthodes sont appelées *opérateurs de requête standard*.  En tant que développeur, vous pouvez les appeler directement en utilisant la syntaxe de méthode plutôt que la syntaxe de requête. Pour plus d'informations, consultez [Query Syntax and Method Syntax in LINQ](../Topic/Query%20Syntax%20and%20Method%20Syntax%20in%20LINQ%20\(C%23\).md).  
  
### Syntaxe d'expression de requête  
 Les expressions de requête utilisent une syntaxe de requête déclarative.  Cette syntaxe permet au développeur d'écrire des requêtes dans un langage de haut niveau formaté de façon similaire à Transact\-SQL.  En utilisant la syntaxe d'expression de requête, vous pouvez même effectuer des opérations de filtrage, de classement et de regroupement complexes sur des sources de données avec un minimum de code.  Pour plus d'informations, consultez [Opérations de requête de base \(Visual Basic\)](../Topic/Basic%20Query%20Operations%20\(Visual%20Basic\).md).  Pour obtenir des exemples d'utilisation de la syntaxe d'expression de requête, consultez les rubriques suivantes :  
  
-   [Exemples de syntaxe d'expression de requête : projection](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [Exemples de syntaxe d'expression de requête : filtrage](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [Exemples de syntaxe d'expression de requête : classement](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [Exemples de syntaxe d'expression de requête : opérateurs d'agrégation](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [Exemples de syntaxe d'expression de requête : partitionnement](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [Exemples de syntaxe d'expression de requête : opérateurs de jointure](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [Exemples de syntaxe d'expression de requête : opérateurs d'élément](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [Exemples de syntaxe d'expression de requête : regroupement](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [Exemples de syntaxe d'expression de requête : exploration de relations](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### Syntaxe de requête fondée sur une méthode  
 Une autre manière de composer des requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] consiste à utiliser des requêtes fondées sur une méthode.  La syntaxe de requête fondée sur une méthode est une séquence d'appels directs de méthodes d'opérateur LINQ passant des expressions lambda comme paramètres.  Pour plus d'informations, consultez [Expressions lambda](../Topic/Lambda%20Expressions%20\(C%23%20Programming%20Guide\).md).  Pour obtenir des exemples d'utilisation de la syntaxe fondée sur une méthode, consultez les rubriques suivantes :  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : projection](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : filtrage](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : classement](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'agrégation](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : partitionnement](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : conversion](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : opérateurs de jointure](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'élément](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : regroupement](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [Exemples de syntaxe de requête fondée sur une méthode : exploration de relations](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## Voir aussi  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)   
 [Getting Started with LINQ in C\#](../Topic/Getting%20Started%20with%20LINQ%20in%20C%23.md)   
 [Getting Started with LINQ in Visual Basic](../Topic/Getting%20Started%20with%20LINQ%20in%20Visual%20Basic.md)   
 [Options de fusion Entity Framework et requêtes compilées](http://go.microsoft.com/fwlink/?LinkId=199591)