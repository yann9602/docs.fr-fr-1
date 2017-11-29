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
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="673ff-102">Comment : accéder à un membre à l'aide d'un pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="673ff-102">How to: Access a Member with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="673ff-103">Pour accéder à un membre d’un struct déclaré dans un contexte unsafe, vous pouvez utiliser l’opérateur d’accès au membre comme illustré dans l’exemple suivant où `p` est un pointeur vers un [struct](../../../csharp/language-reference/keywords/struct.md) qui contient un membre `x`.</span><span class="sxs-lookup"><span data-stu-id="673ff-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="673ff-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="673ff-104">Example</span></span>  
 <span data-ttu-id="673ff-105">Dans cet exemple, un [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, qui contient les deux coordonnées `x` et `y`, est déclaré et instancié.</span><span class="sxs-lookup"><span data-stu-id="673ff-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="673ff-106">En utilisant l’opérateur d’accès au membre `->` et un pointeur vers l’instance `home`, `x` et `y` sont des valeurs assignées.</span><span class="sxs-lookup"><span data-stu-id="673ff-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="673ff-107">Remarquez que l’expression `p->x` équivaut à l’expression `(*p).x`, et vous pouvez obtenir le même résultat en utilisant l’une ou l’autre expression.</span><span class="sxs-lookup"><span data-stu-id="673ff-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="673ff-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="673ff-108">See Also</span></span>  
 [<span data-ttu-id="673ff-109">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="673ff-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="673ff-110">Expressions de pointeur</span><span class="sxs-lookup"><span data-stu-id="673ff-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="673ff-111">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="673ff-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="673ff-112">Types</span><span class="sxs-lookup"><span data-stu-id="673ff-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="673ff-113">unsafe</span><span class="sxs-lookup"><span data-stu-id="673ff-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="673ff-114">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="673ff-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="673ff-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="673ff-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
