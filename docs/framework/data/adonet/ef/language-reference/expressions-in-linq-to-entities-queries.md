---
title: "Expressions dans les requêtes LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2f429a354c4042f0e85b9ef078bbc57ebe510d0d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="expressions-in-linq-to-entities-queries"></a>Expressions dans les requêtes LINQ to Entities
Une expression est un fragment de code qui peut correspondre à une valeur, un objet, une méthode ou un espace de noms. Elle peut contenir une valeur littérale, un appel de méthode, un opérateur et ses opérandes ou un nom simple. Un nom simple peut être le nom d'une variable, d'un membre de type, d'un paramètre de méthode, d'un espace de noms ou d'un type. Les expressions peuvent utiliser des opérateurs qui à leur tour utilisent d'autres expressions comme des paramètres, ou des appels de méthode dont les paramètres sont à leur tour d'autres appels de méthode. Par conséquent, les expressions peuvent être simples ou très complexes.  
  
 Dans [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] des requêtes, les expressions peuvent contenir tout élément autorisé par les types dans les <xref:System.Linq.Expressions> espace de noms, y compris des expressions lambda. Les expressions utilisables dans les requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sont un surensemble des expressions qui permettent d'interroger [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Les expressions qui font partie des requêtes sur le [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] sont limitées aux opérations prises en charge par `ObjectQuery<T>` et la source de données sous-jacente.  
  
 Dans l'exemple suivant, la comparaison dans la clause `Where` est une expression :  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Les constructions de langage spécifiques, telles que C# `unchecked`, n'ont aucune signification dans [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Expressions de constantes](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Expressions de comparaison](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Comparaisons Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Expressions d’initialisation](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Propriétés de navigation](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a>Voir aussi  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
