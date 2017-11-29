---
title: "Comment : accéder à un membre à l'aide d'un pointeur (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 622d9910b09c9197b7f4ccd5e54e2675fbbbbccb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Comment : accéder à un membre à l'aide d'un pointeur (Guide de programmation C#)
Pour accéder à un membre d’un struct déclaré dans un contexte unsafe, vous pouvez utiliser l’opérateur d’accès au membre comme illustré dans l’exemple suivant où `p` est un pointeur vers un [struct](../../../csharp/language-reference/keywords/struct.md) qui contient un membre `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, un [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, qui contient les deux coordonnées `x` et `y`, est déclaré et instancié. En utilisant l’opérateur d’accès au membre `->` et un pointeur vers l’instance `home`, `x` et `y` sont des valeurs assignées.  
  
> [!NOTE]
>  Remarquez que l’expression `p->x` équivaut à l’expression `(*p).x`, et vous pouvez obtenir le même résultat en utilisant l’une ou l’autre expression.  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Types de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Types](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
