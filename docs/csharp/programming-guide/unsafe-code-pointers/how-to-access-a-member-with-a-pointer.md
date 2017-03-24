---
title: "Comment&#160;: acc&#233;der &#224; un membre &#224; l&#39;aide d&#39;un pointeur (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "pointeurs (C#), accès aux membres"
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# Comment&#160;: acc&#233;der &#224; un membre &#224; l&#39;aide d&#39;un pointeur (Guide de programmation C#)
Pour accéder à un membre d'une structure déclarée dans un contexte unsafe, vous pouvez utiliser l'opérateur d'accès au membre comme illustré dans l'exemple suivant où `p` est un pointeur vers une [structure](../../../csharp/language-reference/keywords/struct.md) contenant un membre `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## Exemple  
 Dans cet exemple, une [structure](../../../csharp/language-reference/keywords/struct.md), `CoOrds` qui contient les deux coordonnées `x` et `y`, est déclarée et instanciée.  En utilisant l'opérateur d'accès au membre `->` et un pointeur vers l'instance `home`, `x` et `y` sont des valeurs assignées.  
  
> [!NOTE]
>  Remarquez que l'expression `p->x` équivaut à l'expression `(*p).x`, et vous pouvez obtenir le même résultat en utilisant l'une ou l'autre expression.  
  
 [!code-cs[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-cs[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)