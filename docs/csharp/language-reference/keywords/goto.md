---
title: "goto (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
dev_langs:
- CSharp
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cd298809ab883f425f3bb88239f2951ab98cc03e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="goto-c-reference"></a>goto (référence C#)
L’instruction `goto` transfère le contrôle du programme directement à une instruction étiquetée.  
  
 Une utilisation courante de `goto` consiste à transférer le contrôle à une étiquette switch-case ou à l’étiquette par défaut d’une instruction `switch`.  
  
 L’instruction `goto` sert aussi à quitter des boucles fortement imbriquées.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser `goto` dans une instruction [switch](../../../csharp/language-reference/keywords/switch.md).  
  
 [!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser `goto` pour quitter des boucles imbriquées.  
  
 [!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [GoTo, instruction](/cpp/cpp/goto-statement-cpp)   
 [Instructions de saut](../../../csharp/language-reference/keywords/jump-statements.md)

