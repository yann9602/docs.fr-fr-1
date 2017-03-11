---
title: "Comment&#160;: utiliser des tableaux et des variables locales implicitement typ&#233;s dans une expression de requ&#234;te (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "variables locales implicitement typées (C#), comment utiliser"
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# Comment&#160;: utiliser des tableaux et des variables locales implicitement typ&#233;s dans une expression de requ&#234;te (Guide de programmation&#160;C#)
Vous pouvez utiliser des variables locales implicitement typées à chaque fois que vous souhaitez que le compilateur détermine le type d'une variable locale.  Vous devez utiliser des variables locales implicitement typées pour stocker des types anonymes, qui sont souvent utilisés dans les expressions de requête.  Les exemples suivants illustrent les utilisations facultative et requise des variables locales implicitement typées dans des requêtes.  
  
 Les variables locales implicitement typées sont déclarées en utilisant le mot clé contextuel [var](../../../csharp/language-reference/keywords/var.md).  Pour plus d'informations, consultez [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) et [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## Exemple  
 L'exemple suivant présente un scénario courant dans lequel le mot clé `var` est requis : une expression de requête qui produit une séquence de types anonymes.  Dans ce scénario, la variable de requête et la variable d'itération dans l'instruction `foreach` doivent être implicitement typées en utilisant `var` parce que vous n'avez pas accès à un nom de type du type anonyme.  Pour plus d'informations sur les types anonymes, consultez [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 [!code-cs[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#32)]  
  
## Exemple  
 L'exemple suivant utilise le mot clé `var` dans une situation de similaire, mais dans laquelle l'utilisation de `var` est facultative.  Dans la mesure où `student.LastName` est une chaîne, l'exécution de la requête retourne une séquence de chaînes.  Par conséquent, le type de `queryID` peut être déclaré comme `System.Collections.Generic.IEnumerable<string>` au lieu de `var`.  Le mot clé `var` est utilisé pour des raisons de commodité.  Dans l'exemple, la variable d'itération dans l'instruction `foreach` est explicitement typée comme chaîne, mais elle peut à la place être déclarée à l'aide de `var`.  Étant donné que le type de la variable d'itération n'est pas un type anonyme, l'utilisation de `var` est une option, pas une obligation.  N'oubliez pas que `var` lui\-même n'est pas un type, mais une instruction demandant au compilateur de déduire et d'assigner le type.  
  
 [!code-cs[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#33)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Méthodes d'extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)