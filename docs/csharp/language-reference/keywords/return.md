---
title: "return (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "return_CSharpKeyword"
  - "return"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "return (mot clé C#)"
  - "return (instruction C#)"
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# return (r&#233;f&#233;rence C#)
L'instruction `return` termine l'exécution de la méthode où elle apparaît et rend le contrôle à la méthode appelante.  Elle peut aussi retourner une valeur optionnelle.  Si la méthode est un type `void`, l'instruction `return` peut être omise.  
  
 Si l'instruction return est à l'intérieur d'un bloc `try`, le bloc `finally`, s'il existe, est exécuté avant que le contrôle retourne à la méthode appelante.  
  
## Exemple  
 Dans l'exemple suivant, la méthode `A()` retourne la variable `Area` comme une valeur [double](../../../csharp/language-reference/keywords/double.md).  
  
 [!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/csharp/return_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [return, instruction](/visual-cpp/cpp/return-statement-cpp)   
 [Instructions de saut](../../../csharp/language-reference/keywords/jump-statements.md)