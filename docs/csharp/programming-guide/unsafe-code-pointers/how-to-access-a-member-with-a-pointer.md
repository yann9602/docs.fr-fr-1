---
title: "Guide pratique pour accéder à un membre à l’aide d’un pointeur (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: 16
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
ms.openlocfilehash: ca24b7d930e7b6c61a3db89a431f1ec3aaec77c8
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Guide pratique pour accéder à un membre à l’aide d’un pointeur (Guide de programmation C#)
Pour accéder à un membre d’un struct déclaré dans un contexte unsafe, vous pouvez utiliser l’opérateur d’accès au membre comme illustré dans l’exemple suivant où `p` est un pointeur vers un [struct](../../../csharp/language-reference/keywords/struct.md) qui contient un membre `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, un [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, qui contient les deux coordonnées `x` et `y`, est déclaré et instancié. En utilisant l’opérateur d’accès au membre `->` et un pointeur vers l’instance `home`, `x` et `y` sont des valeurs assignées.  
  
> [!NOTE]
>  Remarquez que l’expression `p->x` équivaut à l’expression `(*p).x`, et vous pouvez obtenir le même résultat en utilisant l’une ou l’autre expression.  
  
 [!code-cs[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-cs[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)

