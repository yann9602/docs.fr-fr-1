---
title: "while (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
dev_langs:
- CSharp
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
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
ms.openlocfilehash: 744980f2dd55806062901d874a3137f5936e0888
ms.lasthandoff: 03/13/2017

---
# <a name="while-c-reference"></a>while (référence C#)
L’instruction `while` exécute une instruction ou un bloc d’instructions jusqu’à ce qu’une expression spécifique corresponde à la valeur `false`.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>Exemple  
 [!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>Exemple  
 Comme le test de l’expression `while` a lieu avant chaque exécution de la boucle, une boucle `while` est exécutée plusieurs fois ou pas du tout. Cela diffère de la boucle [do](../../../csharp/language-reference/keywords/do.md), qui s’exécute une ou plusieurs fois.  
  
 Une boucle `while` peut être terminée quand une instruction [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md) transfère le contrôle à l’extérieur de la boucle. Pour transmettre le contrôle à la prochaine itération sans sortir de la boucle, utilisez l’instruction [continue](../../../csharp/language-reference/keywords/continue.md). Notez la différence de sortie des trois exemples précédents, selon l’emplacement où `int n` est incrémenté. Dans l’exemple ci-dessous, aucune sortie n’est générée.  
  
 [!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [while, instruction (C++)](https://docs.microsoft.com/cpp/cpp/while-statement-cpp)   
 [Instructions d’itération](../../../csharp/language-reference/keywords/iteration-statements.md)
