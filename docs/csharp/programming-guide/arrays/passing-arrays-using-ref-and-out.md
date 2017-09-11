---
title: "Passage de tableaux à l'aide de paramètres ref et out (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
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
ms.openlocfilehash: 58fc359881295a9e6627ac1269ef17aa298009c7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="9c440-102">Passage de tableaux à l'aide de paramètres ref et out (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9c440-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>
<span data-ttu-id="9c440-103">Comme tous les paramètres [out](../../../csharp/language-reference/keywords/out.md), un paramètre `out` d’un type tableau doit être assigné avant d’être utilisé ; c’est-à-dire qu’il doit être assigné par l’appelé.</span><span class="sxs-lookup"><span data-stu-id="9c440-103">Like all [out](../../../csharp/language-reference/keywords/out.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="9c440-104">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9c440-104">For example:</span></span>  
  
 <span data-ttu-id="9c440-105">[!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9c440-105">[!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]</span></span>  
  
 <span data-ttu-id="9c440-106">Comme tous les paramètres [ref](../../../csharp/language-reference/keywords/ref.md), un paramètre `ref` d’un type tableau doit absolument être assigné par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="9c440-106">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="9c440-107">Par conséquent, il n'a pas besoin d'être assigné par l'appelé.</span><span class="sxs-lookup"><span data-stu-id="9c440-107">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="9c440-108">Un paramètre `ref` d'un type tableau peut être modifié à la suite de l'appel.</span><span class="sxs-lookup"><span data-stu-id="9c440-108">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="9c440-109">Par exemple, la valeur [null](../../../csharp/language-reference/keywords/null.md) peut être assignée au tableau ou ce dernier peut être initialisé sur un tableau différent.</span><span class="sxs-lookup"><span data-stu-id="9c440-109">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="9c440-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9c440-110">For example:</span></span>  
  
 <span data-ttu-id="9c440-111">[!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9c440-111">[!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]</span></span>  
  
 <span data-ttu-id="9c440-112">Les deux exemples suivants illustrent la différence entre les paramètres `out` et `ref` lorsqu'ils sont utilisés pour le passage de tableaux à des méthodes.</span><span class="sxs-lookup"><span data-stu-id="9c440-112">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c440-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c440-113">Example</span></span>  
 <span data-ttu-id="9c440-114">Dans cet exemple, le tableau `theArray` est déclaré dans l'appelant (la méthode `Main`) et initialisé dans la méthode `FillArray`.</span><span class="sxs-lookup"><span data-stu-id="9c440-114">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="9c440-115">Ensuite, les éléments du tableau sont retournés à l'appelant puis affichés.</span><span class="sxs-lookup"><span data-stu-id="9c440-115">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 <span data-ttu-id="9c440-116">[!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9c440-116">[!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c440-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c440-117">Example</span></span>  
 <span data-ttu-id="9c440-118">Dans cet exemple, le tableau `theArray` est initialisé dans l'appelant (la méthode `Main`) et passé à la méthode `FillArray` à l'aide du paramètre `ref`.</span><span class="sxs-lookup"><span data-stu-id="9c440-118">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="9c440-119">Certains des éléments du tableau sont mis à jour dans la méthode `FillArray`.</span><span class="sxs-lookup"><span data-stu-id="9c440-119">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="9c440-120">Ensuite, les éléments du tableau sont retournés à l'appelant puis affichés.</span><span class="sxs-lookup"><span data-stu-id="9c440-120">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 <span data-ttu-id="9c440-121">[!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="9c440-121">[!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c440-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c440-122">See Also</span></span>  
 <span data-ttu-id="9c440-123">[ref](../../../csharp/language-reference/keywords/ref.md) </span><span class="sxs-lookup"><span data-stu-id="9c440-123">[ref](../../../csharp/language-reference/keywords/ref.md) </span></span>  
 <span data-ttu-id="9c440-124">[out, modificateur de paramètre](../../../csharp/language-reference/keywords/out-parameter-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="9c440-124">[out parameter modifier](../../../csharp/language-reference/keywords/out-parameter-modifier.md) </span></span>  
 <span data-ttu-id="9c440-125">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9c440-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9c440-126">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="9c440-126">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="9c440-127">[Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="9c440-127">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 <span data-ttu-id="9c440-128">[Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="9c440-128">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="9c440-129">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="9c440-129">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

