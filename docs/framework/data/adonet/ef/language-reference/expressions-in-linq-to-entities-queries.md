---
title: "Expressions dans les requ&#234;tes LINQ to Entities | Microsoft Docs"
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
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Expressions dans les requ&#234;tes LINQ to Entities
Une expression est un fragment de code qui peut correspondre à une valeur, un objet, une méthode ou un espace de noms.  Elle peut contenir une valeur littérale, un appel de méthode, un opérateur et ses opérandes ou un nom simple.  Un nom simple peut être le nom d'une variable, d'un membre de type, d'un paramètre de méthode, d'un espace de noms ou d'un type.  Les expressions peuvent utiliser des opérateurs qui à leur tour utilisent d'autres expressions comme des paramètres, ou des appels de méthode dont les paramètres sont à leur tour d'autres appels de méthode.  Par conséquent, les expressions peuvent être simples ou très complexes.  
  
 Dans les requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], les expressions peuvent contenir tout élément autorisé par les types de l'espace de noms <xref:System.Linq.Expressions>, y compris des expressions lambda.  Les expressions utilisables dans les requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sont un surensemble des expressions qui permettent d'interroger [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Les expressions qui font partie des requêtes sur [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] sont limitées aux opérations prises en charge par `ObjectQuery<T>` et la source de données sous\-jacente.  
  
 Dans l'exemple suivant, la comparaison dans la clause `Where` est une expression :  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Les constructions de langage spécifiques, telles que C\# `unchecked`, n'ont aucune signification dans [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## Dans cette section  
 [Expressions constantes](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Expressions de comparaison](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Comparaisons de valeurs Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Expressions d'initialisation](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Navigation Properties](http://msdn.microsoft.com/fr-fr/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## Voir aussi  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)