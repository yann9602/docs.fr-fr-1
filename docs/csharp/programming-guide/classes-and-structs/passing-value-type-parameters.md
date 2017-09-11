---
title: "Passage de paramètres de type valeur (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
caps.latest.revision: 17
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
ms.openlocfilehash: a3377630fc4294831f6b9d66a69377aa42d973f1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="passing-value-type-parameters-c-programming-guide"></a><span data-ttu-id="d9cc4-102">Passage de paramètres de type valeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d9cc4-102">Passing Value-Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="d9cc4-103">Une variable de [type valeur](../../../csharp/language-reference/keywords/value-types.md) contient ses données directement, par opposition à une variable de [type référence](../../../csharp/language-reference/keywords/reference-types.md), qui contient une référence à ses données.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-103">A [value-type](../../../csharp/language-reference/keywords/value-types.md) variable contains its data directly as opposed to a [reference-type](../../../csharp/language-reference/keywords/reference-types.md) variable, which contains a reference to its data.</span></span> <span data-ttu-id="d9cc4-104">Passer une variable de type valeur à une méthode par valeur signifie passer une copie de la variable à la méthode.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-104">Passing a value-type variable to a method by value means passing a copy of the variable to the method.</span></span> <span data-ttu-id="d9cc4-105">Les modifications du paramètre qui interviennent à l’intérieur de la méthode n’ont aucune incidence sur les données d’origine stockées dans la variable d’argument.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-105">Any changes to the parameter that take place inside the method have no affect on the original data stored in the argument variable.</span></span> <span data-ttu-id="d9cc4-106">Si vous souhaitez que la méthode appelée change la valeur du paramètre, vous devez la passer par référence, à l’aide du mot clé [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).</span><span class="sxs-lookup"><span data-stu-id="d9cc4-106">If you want the called method to change the value of the parameter, you must pass it by reference, using the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) keyword.</span></span> <span data-ttu-id="d9cc4-107">Pour des raisons de simplicité, les exemples suivants utilisent `ref`.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-107">For simplicity, the following examples use `ref`.</span></span>  
  
## <a name="passing-value-types-by-value"></a><span data-ttu-id="d9cc4-108">Passage de types valeur par valeur</span><span class="sxs-lookup"><span data-stu-id="d9cc4-108">Passing Value Types by Value</span></span>  
 <span data-ttu-id="d9cc4-109">L’exemple suivant illustre le passage de paramètres de type valeur par valeur.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-109">The following example demonstrates passing value-type parameters by value.</span></span> <span data-ttu-id="d9cc4-110">La variable `n` est passée par valeur à la méthode `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-110">The variable `n` is passed by value to the method `SquareIt`.</span></span> <span data-ttu-id="d9cc4-111">Les modifications qui interviennent à l’intérieur de la méthode n’ont aucune incidence sur la valeur d’origine de la variable.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-111">Any changes that take place inside the method have no affect on the original value of the variable.</span></span>  
  
 <span data-ttu-id="d9cc4-112">[!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d9cc4-112">[!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]</span></span>  
  
 <span data-ttu-id="d9cc4-113">La variable `n` est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-113">The variable `n` is a value type.</span></span> <span data-ttu-id="d9cc4-114">Elle contient ses données, la valeur `5`.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-114">It contains its data, the value `5`.</span></span> <span data-ttu-id="d9cc4-115">Quand `SquareIt` est appelée, le contenu de `n` est copié dans le paramètre `x`, qui est mis au carré à l’intérieur de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-115">When `SquareIt` is invoked, the contents of `n` are copied into the parameter `x`, which is squared inside the method.</span></span> <span data-ttu-id="d9cc4-116">Dans `Main`, toutefois, la valeur de `n` est identique avant et après l’appel de la méthode `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-116">In `Main`, however, the value of `n` is the same after calling the `SquareIt` method as it was before.</span></span> <span data-ttu-id="d9cc4-117">La modification qui intervient à l’intérieur de la méthode affecte uniquement la variable locale `x`.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-117">The change that takes place inside the method only affects the local variable `x`.</span></span>  
  
## <a name="passing-value-types-by-reference"></a><span data-ttu-id="d9cc4-118">Passage de types valeur par référence</span><span class="sxs-lookup"><span data-stu-id="d9cc4-118">Passing Value Types by Reference</span></span>  
 <span data-ttu-id="d9cc4-119">L’exemple suivant est identique au précédent, sauf que l’argument est passé en tant que paramètre `ref`.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-119">The following example is the same as the previous example, except that the argument is passed as a `ref` parameter.</span></span> <span data-ttu-id="d9cc4-120">La valeur de l’argument sous-jacent, `n`, est modifiée quand `x` est modifiée dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-120">The value of the underlying argument, `n`, is changed when `x` is changed in the method.</span></span>  
  
 <span data-ttu-id="d9cc4-121">[!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d9cc4-121">[!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]</span></span>  
  
 <span data-ttu-id="d9cc4-122">Dans cet exemple, ce n’est pas la valeur de `n` qui est passée, mais plutôt une référence à `n`.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-122">In this example, it is not the value of `n` that is passed; rather, a reference to `n` is passed.</span></span> <span data-ttu-id="d9cc4-123">Le paramètre `x` n’est pas un [int](../../../csharp/language-reference/keywords/int.md) ; il s’agit d’une référence à un `int`, dans le cas présent une référence à `n`.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-123">The parameter `x` is not an [int](../../../csharp/language-reference/keywords/int.md); it is a reference to an `int`, in this case, a reference to `n`.</span></span> <span data-ttu-id="d9cc4-124">Ainsi, quand `x` est mis au carré à l’intérieur de la méthode, ce qui est réellement mis au carré est ce à quoi `x` fait référence, c’est-à-dire `n`.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-124">Therefore, when `x` is squared inside the method, what actually is squared is what `x` refers to, `n`.</span></span>  
  
## <a name="swapping-value-types"></a><span data-ttu-id="d9cc4-125">Permutation de types valeur</span><span class="sxs-lookup"><span data-stu-id="d9cc4-125">Swapping Value Types</span></span>  
 <span data-ttu-id="d9cc4-126">L’un des exemples courants de changement de valeurs d’arguments est une méthode de permutation, où vous passez deux variables à la méthode et celle-ci permute leur contenu.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-126">A common example of changing the values of arguments is a swap method, where you pass two variables to the method, and the method swaps their contents.</span></span> <span data-ttu-id="d9cc4-127">Vous devez passer les arguments à la méthode de permutation par référence.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-127">You must pass the arguments to the swap method by reference.</span></span> <span data-ttu-id="d9cc4-128">Sinon, vous permutez des copies locales des paramètres à l’intérieur de la méthode, et aucune modification n’intervient dans la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-128">Otherwise, you swap local copies of the parameters inside the method, and no change occurs in the calling method.</span></span> <span data-ttu-id="d9cc4-129">L’exemple suivant permute des valeurs d’entier.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-129">The following example swaps integer values.</span></span>  
  
 <span data-ttu-id="d9cc4-130">[!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="d9cc4-130">[!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]</span></span>  
  
 <span data-ttu-id="d9cc4-131">Quand vous appelez la méthode `SwapByRef`, utilisez le mot-clé `ref` dans l’appel, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d9cc4-131">When you call the `SwapByRef` method, use the `ref` keyword in the call, as shown in the following example.</span></span>  
  
 <span data-ttu-id="d9cc4-132">[!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="d9cc4-132">[!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9cc4-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9cc4-133">See Also</span></span>  
 <span data-ttu-id="d9cc4-134">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d9cc4-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d9cc4-135">[Passage de paramètres](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="d9cc4-135">[Passing Parameters](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span></span>  
 [<span data-ttu-id="d9cc4-136">Passage de paramètres de type référence</span><span class="sxs-lookup"><span data-stu-id="d9cc4-136">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)

