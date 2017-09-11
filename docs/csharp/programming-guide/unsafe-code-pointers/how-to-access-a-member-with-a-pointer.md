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
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="56fec-102">Guide pratique pour accéder à un membre à l’aide d’un pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="56fec-102">How to: Access a Member with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="56fec-103">Pour accéder à un membre d’un struct déclaré dans un contexte unsafe, vous pouvez utiliser l’opérateur d’accès au membre comme illustré dans l’exemple suivant où `p` est un pointeur vers un [struct](../../../csharp/language-reference/keywords/struct.md) qui contient un membre `x`.</span><span class="sxs-lookup"><span data-stu-id="56fec-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="56fec-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="56fec-104">Example</span></span>  
 <span data-ttu-id="56fec-105">Dans cet exemple, un [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, qui contient les deux coordonnées `x` et `y`, est déclaré et instancié.</span><span class="sxs-lookup"><span data-stu-id="56fec-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="56fec-106">En utilisant l’opérateur d’accès au membre `->` et un pointeur vers l’instance `home`, `x` et `y` sont des valeurs assignées.</span><span class="sxs-lookup"><span data-stu-id="56fec-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56fec-107">Remarquez que l’expression `p->x` équivaut à l’expression `(*p).x`, et vous pouvez obtenir le même résultat en utilisant l’une ou l’autre expression.</span><span class="sxs-lookup"><span data-stu-id="56fec-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 <span data-ttu-id="56fec-108">[!code-cs[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="56fec-108">[!code-cs[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]</span></span>  
  
 <span data-ttu-id="56fec-109">[!code-cs[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="56fec-109">[!code-cs[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fec-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56fec-110">See Also</span></span>  
 <span data-ttu-id="56fec-111">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="56fec-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="56fec-112">[Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="56fec-112">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="56fec-113">[Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="56fec-113">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="56fec-114">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="56fec-114">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="56fec-115">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="56fec-115">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="56fec-116">[fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="56fec-116">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="56fec-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="56fec-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

