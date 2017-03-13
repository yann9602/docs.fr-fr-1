---
title: "while (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "while_CSharpKeyword"
  - "while"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "while (mot clé C#)"
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# while (r&#233;f&#233;rence C#)
L'instruction `while` répète une instruction ou un bloc d'instructions jusqu'à ce qu'une expression spécifique corresponde à la valeur `false`.  
  
## Exemple  
 [!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## Exemple  
 [!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## Exemple  
 Parce que le test de l'expression `while` a lieu avant chaque exécution de la boucle, une boucle `while` est exécutée plusieurs fois ou pas du tout.  Cela diffère de la boucle [do](../../../csharp/language-reference/keywords/do.md), qui s'exécute une ou plusieurs fois.  
  
 Une boucle `while` peut être terminée lorsqu'une instruction [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), ou [throw](../../../csharp/language-reference/keywords/throw.md) transfère le contrôle à l'extérieur de la boucle.  Pour transmettre le contrôle à la prochaine itération sans sortir de la boucle, utilisez l'instruction [continue](../../../csharp/language-reference/keywords/continue.md).  Remarquez la différence de sortie des trois exemples précédents, selon l'emplacement où `int n` est incrémenté.  Dans l'exemple ci\-dessous, aucune sortie n'est générée.  
  
 [!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [while, instruction \(C\+\+\)](/visual-cpp/cpp/while-statement-cpp)   
 [Instructions d'itération](../../../csharp/language-reference/keywords/iteration-statements.md)