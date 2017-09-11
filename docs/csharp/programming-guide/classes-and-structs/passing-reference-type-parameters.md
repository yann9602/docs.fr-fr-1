---
title: "Passage de paramètres de type référence (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: 14
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
ms.openlocfilehash: 3f57dc9f0de6fae6da3ec8e6e6cfdc3a21baeaea
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="passing-reference-type-parameters-c-programming-guide"></a><span data-ttu-id="ed15f-102">Passage de paramètres de type référence (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ed15f-102">Passing Reference-Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="ed15f-103">Une variable d’un [type référence](../../../csharp/language-reference/keywords/reference-types.md) ne contient pas directement ses données ; il contient une référence à ses données.</span><span class="sxs-lookup"><span data-stu-id="ed15f-103">A variable of a [reference type](../../../csharp/language-reference/keywords/reference-types.md) does not contain its data directly; it contains a reference to its data.</span></span> <span data-ttu-id="ed15f-104">Quand vous passez un paramètre de type référence par valeur, il est possible de modifier les données vers lesquelles la référence pointe, comme la valeur d’un membre de classe.</span><span class="sxs-lookup"><span data-stu-id="ed15f-104">When you pass a reference-type parameter by value, it is possible to change the data pointed to by the reference, such as the value of a class member.</span></span> <span data-ttu-id="ed15f-105">En revanche, vous ne pouvez pas modifier la valeur de la référence elle-même. Autrement dit, vous ne pouvez pas utiliser la même référence pour allouer de la mémoire à une nouvelle classe et la faire persister en dehors du bloc.</span><span class="sxs-lookup"><span data-stu-id="ed15f-105">However, you cannot change the value of the reference itself; that is, you cannot use the same reference to allocate memory for a new class and have it persist outside the block.</span></span> <span data-ttu-id="ed15f-106">Pour cela, passez le paramètre en utilisant le mot clé [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).</span><span class="sxs-lookup"><span data-stu-id="ed15f-106">To do that, pass the parameter using the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) keyword.</span></span> <span data-ttu-id="ed15f-107">Pour des raisons de simplicité, les exemples suivants utilisent `ref`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-107">For simplicity, the following examples use `ref`.</span></span>  
  
## <a name="passing-reference-types-by-value"></a><span data-ttu-id="ed15f-108">Passage de types référence par valeur</span><span class="sxs-lookup"><span data-stu-id="ed15f-108">Passing Reference Types by Value</span></span>  
 <span data-ttu-id="ed15f-109">L’exemple suivant illustre le passage d’un paramètre de type référence (`arr`) par valeur, à une méthode (`Change`).</span><span class="sxs-lookup"><span data-stu-id="ed15f-109">The following example demonstrates passing a reference-type parameter, `arr`, by value, to a method, `Change`.</span></span> <span data-ttu-id="ed15f-110">Sachant que le paramètre est une référence à `arr`, il est possible de modifier les valeurs des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="ed15f-110">Because the parameter is a reference to `arr`, it is possible to change the values of the array elements.</span></span> <span data-ttu-id="ed15f-111">Cependant, la tentative de réassignation du paramètre à un emplacement de mémoire différent n’aboutit qu’à l’intérieur de la méthode et n’affecte pas la variable d’origine, `arr`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-111">However, the attempt to reassign the parameter to a different memory location only works inside the method and does not affect the original variable, `arr`.</span></span>  
  
 <span data-ttu-id="ed15f-112">[!code-cs[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ed15f-112">[!code-cs[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]</span></span>  
  
 <span data-ttu-id="ed15f-113">Dans l’exemple précédent, le tableau `arr`, qui est un type référence, est passé à la méthode sans le paramètre `ref`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-113">In the preceding example, the array, `arr`, which is a reference type, is passed to the method without the `ref` parameter.</span></span> <span data-ttu-id="ed15f-114">Dans ce cas, une copie de la référence, qui pointe vers `arr`, est passée à la méthode.</span><span class="sxs-lookup"><span data-stu-id="ed15f-114">In such a case, a copy of the reference, which points to `arr`, is passed to the method.</span></span> <span data-ttu-id="ed15f-115">La sortie montre que la méthode peut modifier le contenu d’un élément du tableau, dans ce cas de `1` à `888`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-115">The output shows that it is possible for the method to change the contents of an array element, in this case from `1` to `888`.</span></span> <span data-ttu-id="ed15f-116">Cependant, si vous allouez une nouvelle portion de mémoire via l’opérateur [new](../../../csharp/language-reference/keywords/new.md) à l’intérieur de la méthode `Change`, la variable `pArray` fait référence à un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="ed15f-116">However, allocating a new portion of memory by using the [new](../../../csharp/language-reference/keywords/new.md) operator inside the `Change` method makes the variable `pArray` reference a new array.</span></span> <span data-ttu-id="ed15f-117">Par conséquent, les modifications apportées à la suite de cette opération n’ont pas d’effet sur le tableau d’origine (`arr`), qui est créé à l’intérieur de `Main`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-117">Thus, any changes after that will not affect the original array, `arr`, which is created inside `Main`.</span></span> <span data-ttu-id="ed15f-118">En fait, deux tableaux sont créés dans cet exemple : un à l’intérieur de `Main` et un autre à l’intérieur de la méthode `Change`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-118">In fact, two arrays are created in this example, one inside `Main` and one inside the `Change` method.</span></span>  
  
## <a name="passing-reference-types-by-reference"></a><span data-ttu-id="ed15f-119">Passage de types référence par référence</span><span class="sxs-lookup"><span data-stu-id="ed15f-119">Passing Reference Types by Reference</span></span>  
 <span data-ttu-id="ed15f-120">L’exemple suivant est identique au précédent, sauf que le mot clé `ref` est ajouté à l’en-tête et à l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ed15f-120">The following example is the same as the previous example, except that the `ref` keyword is added to the method header and call.</span></span> <span data-ttu-id="ed15f-121">Les modifications qui se produisent dans la méthode affectent la variable d’origine dans le programme appelant.</span><span class="sxs-lookup"><span data-stu-id="ed15f-121">Any changes that take place in the method affect the original variable in the calling program.</span></span>  
  
 <span data-ttu-id="ed15f-122">[!code-cs[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ed15f-122">[!code-cs[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]</span></span>  
  
 <span data-ttu-id="ed15f-123">Les modifications qui se produisent à l’intérieur de la méthode affectent le tableau d’origine dans `Main`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-123">All of the changes that take place inside the method affect the original array in `Main`.</span></span> <span data-ttu-id="ed15f-124">En fait, le tableau d’origine est réalloué à l’aide de l’opérateur `new`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-124">In fact, the original array is reallocated using the `new` operator.</span></span> <span data-ttu-id="ed15f-125">Par conséquent, après l’appel à la méthode `Change`, toute référence à `arr` pointe vers le tableau à cinq éléments, qui est créé dans la méthode `Change`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-125">Thus, after calling the `Change` method, any reference to `arr` points to the five-element array, which is created in the `Change` method.</span></span>  
  
## <a name="swapping-two-strings"></a><span data-ttu-id="ed15f-126">Permutation de deux chaînes</span><span class="sxs-lookup"><span data-stu-id="ed15f-126">Swapping Two Strings</span></span>  
 <span data-ttu-id="ed15f-127">La permutation de chaînes est un bon exemple de passage de paramètres de type référence par référence.</span><span class="sxs-lookup"><span data-stu-id="ed15f-127">Swapping strings is a good example of passing reference-type parameters by reference.</span></span> <span data-ttu-id="ed15f-128">Dans l’exemple, deux chaînes, `str1` et `str2`, sont initialisées dans `Main` et passées à la méthode `SwapStrings` en tant que paramètres modifiés par le mot clé `ref`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-128">In the example, two strings, `str1` and `str2`, are initialized in `Main` and passed to the `SwapStrings` method as parameters modified by the `ref` keyword.</span></span> <span data-ttu-id="ed15f-129">Les deux chaînes sont permutées à l’intérieur de la méthode mais aussi à l’intérieur de `Main`.</span><span class="sxs-lookup"><span data-stu-id="ed15f-129">The two strings are swapped inside the method and inside `Main` as well.</span></span>  
  
 <span data-ttu-id="ed15f-130">[!code-cs[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="ed15f-130">[!code-cs[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]</span></span>  
  
 <span data-ttu-id="ed15f-131">Dans cet exemple, les paramètres doivent être passés par référence pour affecter les variables dans le programme appelant.</span><span class="sxs-lookup"><span data-stu-id="ed15f-131">In this example, the parameters need to be passed by reference to affect the variables in the calling program.</span></span> <span data-ttu-id="ed15f-132">Si vous supprimez le mot clé `ref` de l’en-tête et de l’appel de la méthode, aucune modification ne se produit dans le programme appelant.</span><span class="sxs-lookup"><span data-stu-id="ed15f-132">If you remove the `ref` keyword from both the method header and the method call, no changes will take place in the calling program.</span></span>  
  
 <span data-ttu-id="ed15f-133">Pour plus d’informations sur les chaînes, consultez [string](../../../csharp/language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="ed15f-133">For more information about strings, see [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed15f-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed15f-134">See Also</span></span>  
 <span data-ttu-id="ed15f-135">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ed15f-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ed15f-136">[Passage de paramètres](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="ed15f-136">[Passing Parameters](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span></span>  
 <span data-ttu-id="ed15f-137">[Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md) </span><span class="sxs-lookup"><span data-stu-id="ed15f-137">[Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md) </span></span>  
 <span data-ttu-id="ed15f-138">[ref](../../../csharp/language-reference/keywords/ref.md) </span><span class="sxs-lookup"><span data-stu-id="ed15f-138">[ref](../../../csharp/language-reference/keywords/ref.md) </span></span>  
 [<span data-ttu-id="ed15f-139">Types référence</span><span class="sxs-lookup"><span data-stu-id="ed15f-139">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)

