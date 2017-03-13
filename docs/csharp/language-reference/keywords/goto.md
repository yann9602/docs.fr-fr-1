---
title: "goto (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "goto_CSharpKeyword"
  - "goto"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "goto (mot clé C#)"
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# goto (r&#233;f&#233;rence C#)
L'instruction `goto` transfère directement le contrôle du programme à une instruction étiquetée.  
  
 `goto` est utilisé couramment pour transférer le contrôle à une étiquette switch case spécifique ou à une étiquette default dans une instruction `switch`.  
  
 L'instruction `goto` sert aussi à sortir des boucles profondément imbriquées.  
  
## Exemple  
 L'exemple illustre l'utilisation de `goto` dans une instruction [switch](../../../csharp/language-reference/keywords/switch.md).  
  
 [!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de `goto` pour sortir des boucles imbriquées.  
  
 [!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [goto, instruction](/visual-cpp/cpp/goto-statement-cpp)   
 [Instructions de saut](../../../csharp/language-reference/keywords/jump-statements.md)