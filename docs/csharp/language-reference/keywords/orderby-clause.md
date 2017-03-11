---
title: "orderby, clause (R&#233;f&#233;rence&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "orderby"
  - "orderby_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "orderby (clause C#)"
  - "orderby (mot clé C#)"
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# orderby, clause (R&#233;f&#233;rence&#160;C#)
La clause `orderby` entraîne le tri en ordre croissant ou décroissant de la séquence ou de la sous\-séquence \(groupe\) retournées dans une expression de requête.  Plusieurs clés peuvent être spécifiées pour effectuer une ou plusieurs opérations de tri secondaires.  Le tri est effectué par le comparateur par défaut pour le type de l'élément.  L'ordre de tri par défaut est le tri croissant.  Vous pouvez également spécifier un comparateur personnalisé.  Toutefois, il est uniquement disponible en utilisant la syntaxe fondée sur une méthode.  Pour plus d'informations, consultez [Sorting Data](../../../visual-basic/programming-guide/concepts/linq/sorting-data.md).  
  
## Exemple  
 Dans l'exemple suivant, la première requête trie les mots en ordre alphabétique à partir de A et la deuxième requête trie les mêmes mots en ordre décroissant.  Le mot clé `ascending` est la valeur de tri par défaut et peut être omis.  
  
 [!code-cs[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Orderby.cs#20)]  
  
## Exemple  
 L'exemple suivant effectue un tri principal sur les noms des étudiants, puis un tri secondaire sur leurs prénoms.  
  
 [!code-cs[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Orderby.cs#22)]  
  
## Notes  
 À la compilation, la clause `orderby` est traduite en un appel à la méthode <xref:System.Linq.Enumerable.OrderBy%2A>.  Plusieurs clés dans la clause `orderby` se traduisent en appels de méthode <xref:System.Linq.Enumerable.ThenBy%2A>.  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Mots clés de requête \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group, clause](../../../csharp/language-reference/keywords/group-clause.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)