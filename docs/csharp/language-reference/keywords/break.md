---
title: "break (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1ad255ce1b57da81b791897044d1038f0ef4981a
ms.lasthandoff: 03/13/2017

---
# <a name="break-c-reference"></a>break (référence C#)
L’instruction `break` termine la boucle englobante ou l’instruction [switch](../../../csharp/language-reference/keywords/switch.md) la plus proche dans laquelle elle figure. Le contrôle est passé à l’instruction qui suit l’instruction terminée, le cas échéant.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l’instruction conditionnelle contient un compteur qui est supposé compter de 1 à 100. Toutefois, l’instruction `break` termine la boucle après le chiffre 4.  
  
 [!code-cs[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l’instruction `break` est utilisée pour sortir d’une boucle imbriquée interne et passer le contrôle à la boucle externe.  
  
 [!code-cs[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre l’utilisation de `break` dans une instruction [switch](../../../csharp/language-reference/keywords/switch.md).  
  
 [!code-cs[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 Si vous aviez entré `4`, le résultat serait le suivant :  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [switch](../../../csharp/language-reference/keywords/switch.md)   
 [Instructions de saut](../../../csharp/language-reference/keywords/jump-statements.md)   
 [Instructions d’itération](../../../csharp/language-reference/keywords/iteration-statements.md)
