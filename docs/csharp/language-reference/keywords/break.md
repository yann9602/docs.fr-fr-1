---
title: "break (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "break"
  - "break_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "break (mot clé C#)"
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# break (r&#233;f&#233;rence C#)
L'instruction `break` termine la boucle englobante la plus proche ou l'instruction [switch](../../../csharp/language-reference/keywords/switch.md) dans laquelle elle apparaît.  Le contrôle est transmis à l'instruction qui suit l'instruction terminée, s'il y en a une.  
  
## Exemple  
 Dans cet exemple, l'instruction conditionnelle contient un compteur qui est supposé compter de 1 à 100 ; toutefois, l'instruction `break` termine la boucle après 4 comptes.  
  
 [!code-cs[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/csharp/break_1.cs)]  
  
## Exemple  
 Dans cet exemple, l'instruction `break` est utilisée pour sortir d'une boucle imbriquée interne et retourner le contrôle vers la boucle externe.  
  
 [!code-cs[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/csharp/break_2.cs)]  
  
## Exemple  
 Cet exemple montre l'utilisation de `break` dans une instruction [switch](../../../csharp/language-reference/keywords/switch.md).  
  
 [!code-cs[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/csharp/break_3.cs)]  
  
 Si vous entrez la valeur `4`, le résultat serait le suivant :  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [switch](../../../csharp/language-reference/keywords/switch.md)   
 [Instructions de saut](../../../csharp/language-reference/keywords/jump-statements.md)   
 [Instructions d'itération](../../../csharp/language-reference/keywords/iteration-statements.md)