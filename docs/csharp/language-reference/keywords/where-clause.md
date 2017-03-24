---
title: "where, clause (R&#233;f&#233;rence&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "whereclause_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Where (clause C#)"
  - "where (mot clé C#)"
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# where, clause (R&#233;f&#233;rence&#160;C#)
La clause `where` est utilisée dans une expression de requête pour spécifier les éléments de la source de données qui seront retournés dans l'expression de requête.  Il applique une condition booléenne \(*prédicat*\) à chaque élément source \(référencé par la variable de portée\) et retourne ceux pour lesquels la condition spécifiée est remplie.  Une expression de requête unique peut contenir plusieurs clauses `where` et une clause unique peuvent contenir plusieurs sous\-expressions de prédicat.  
  
## Exemple  
 Dans l'exemple suivant, la clause `where` élimine par filtrage tous les nombres excepté ceux inférieurs à cinq.  Si vous supprimez la clause `where`, tous les nombres de la source de données seront retournés.  L'expression `num < 5` est le prédicat qui est appliqué à chaque élément.  
  
 [!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## Exemple  
 Dans une clause `where`  unique, vous pouvez spécifier autant de prédicats que nécessaire à l'aide des opérateurs [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) et [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md).  Dans l'exemple suivant, la requête spécifie deux prédicats pour sélectionner uniquement les nombres pairs inférieurs à cinq.  
  
 [!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## Exemple  
 Une clause `where` peut contenir une ou plusieurs méthodes qui retournent des valeurs booléennes.  Dans l'exemple suivant, la clause `where` utilise une méthode pour déterminer si la valeur actuelle de la variable de portée est paire ou impaire.  
  
 [!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## Notes  
 La clause `where` est un mécanisme de filtrage.  Elle peut être placée à presque n'importe quel endroit d'une expression de requête, sauf qu'elle ne peut pas être la première ni la dernière clause.  Une clause `where` peut apparaître avant ou après une clause [group](../../../csharp/language-reference/keywords/group-clause.md) selon que vous devez ou non filtrer les éléments de la source avant ou après qu'ils soient regroupés.  
  
 Si un prédicat spécifié n'est pas valide pour les éléments de la source de données, une erreur de compilation est générée.  C'est l'un des avantages de la vérification de type fort fourni par [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)].  
  
 À la compilation, le mot clé `where` est converti en un appel à la méthode d'opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A>.  
  
## Voir aussi  
 [Mots clés de requête \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [from, clause](../../../csharp/language-reference/keywords/from-clause.md)   
 [select, clause](../../../csharp/language-reference/keywords/select-clause.md)   
 [Filtering Data](../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)