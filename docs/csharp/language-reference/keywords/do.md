---
title: "do (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "do_CSharpKeyword"
  - "do"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "do (mot clé C#)"
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# do (r&#233;f&#233;rence C#)
L'instruction `do` répète une instruction ou un bloc d'instructions jusqu'à ce qu'une expression spécifique corresponde à la valeur `false`.  Le corps de la boucle doit être placé entre accolades `{}` à moins qu'il se compose d'une instruction unique.  Dans ce cas, les accolades sont facultatives.  
  
## Exemple  
 Dans l'exemple suivant, les instructions de boucle `do-while` s'exécutent tant que la variable `x` est inférieure à 5.  
  
 [!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/csharp/do_1.cs)]  
  
 Contrairement à l'instruction [while](../../../csharp/language-reference/keywords/while.md), une boucle `do-while` est exécutée une fois avant que l'expression conditionnelle ne soit évaluée.  
  
 À tout endroit du bloc `do-while`, vous pouvez sortir de la boucle à l'aide de l'instruction [break](../../../csharp/language-reference/keywords/break.md).  Vous pouvez passer directement à l'instruction d'évaluation d'une expression `while` à, l'aide de l'instruction [continue](../../../csharp/language-reference/keywords/continue.md).  Si l'expression `while` est analysée comme true, l'exécution se poursuit à la première instruction après la boucle.  Si l'expression est analysée comme false, l'exécution se poursuit à la première instruction après la boucle `do-while`.  
  
 Une boucle `do-while` peut également être quittée à l'aide des instructions [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [do\-while, instruction \(C\+\+\)](/visual-cpp/cpp/do-while-statement-cpp)   
 [Instructions d'itération](../../../csharp/language-reference/keywords/iteration-statements.md)