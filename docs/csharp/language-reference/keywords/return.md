---
title: "return (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
dev_langs:
- CSharp
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: 18
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ce15455381a3279a8c77eaa1fb25494cfe5dfc2b
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="return-c-reference"></a>return (référence C#)
L’instruction `return` met un terme à l’exécution de la méthode dans laquelle elle apparaît et retourne le contrôle à la méthode d’appel. Elle peut également retourner une valeur facultative. Si la méthode est un type `void`, l’instruction `return` peut être omise.  
  
 Si l’instruction return est à l’intérieur d’un bloc `try`, le bloc `finally`, le cas échéant, est exécuté avant que le contrôle retourne à la méthode d’appel.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la méthode `A()` retourne la variable `Area` en tant que valeur [double](../../../csharp/language-reference/keywords/double.md).  
  
 [!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [return, instruction](https://docs.microsoft.com/cpp/cpp/return-statement-cpp)   
 [Instructions de saut](../../../csharp/language-reference/keywords/jump-statements.md)
