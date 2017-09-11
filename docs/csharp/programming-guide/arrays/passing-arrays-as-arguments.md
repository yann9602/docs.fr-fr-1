---
title: "Passage de tableaux en tant qu’arguments (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 21
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
ms.openlocfilehash: 5e83c0c119bc1448be76f83416098158c7f5d684
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="2bd7f-102">Passage de tableaux en tant qu’arguments (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2bd7f-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="2bd7f-103">Les tableaux peuvent être passés en tant qu’arguments à des paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="2bd7f-104">Comme les tableaux sont des types référence, la méthode peut modifier la valeur des éléments.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="2bd7f-105">Passage de tableaux unidimensionnels en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="2bd7f-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="2bd7f-106">Vous pouvez passer un tableau unidimensionnel initialisé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="2bd7f-107">Par exemple, l’instruction suivante envoie un tableau à une méthode Print.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-107">For example, the following statement sends an array to a print method.</span></span>  
  
 <span data-ttu-id="2bd7f-108">[!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bd7f-108">[!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]</span></span>  
  
 <span data-ttu-id="2bd7f-109">Le code suivant illustre une implémentation partielle de la méthode Print.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-109">The following code shows a partial implementation of the print method.</span></span>  
  
 <span data-ttu-id="2bd7f-110">[!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bd7f-110">[!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]</span></span>  
  
 <span data-ttu-id="2bd7f-111">Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-111">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 <span data-ttu-id="2bd7f-112">[!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bd7f-112">[!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bd7f-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bd7f-113">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2bd7f-114">Description</span><span class="sxs-lookup"><span data-stu-id="2bd7f-114">Description</span></span>  
 <span data-ttu-id="2bd7f-115">Dans l’exemple suivant, un tableau de chaînes est initialisé et passé en tant qu’argument à une méthode `PrintArray` pour des chaînes.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-115">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="2bd7f-116">La méthode affiche les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-116">The method displays the elements of the array.</span></span> <span data-ttu-id="2bd7f-117">Ensuite, les méthodes `ChangeArray` et `ChangeArrayElement` sont appelées pour montrer que l’envoi d’un argument de tableau par valeur n’empêche pas les modifications au niveau des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-117">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2bd7f-118">Code</span><span class="sxs-lookup"><span data-stu-id="2bd7f-118">Code</span></span>  
 <span data-ttu-id="2bd7f-119">[!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bd7f-119">[!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]</span></span>  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="2bd7f-120">Passage de tableaux multidimensionnels en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="2bd7f-120">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="2bd7f-121">Vous pouvez passer un tableau multidimensionnel initialisé à une méthode de la même manière que vous passez un tableau unidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-121">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 <span data-ttu-id="2bd7f-122">[!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bd7f-122">[!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]</span></span>  
  
 <span data-ttu-id="2bd7f-123">Le code suivant illustre une déclaration partielle d’une méthode Print qui accepte un tableau à deux dimensions en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-123">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 <span data-ttu-id="2bd7f-124">[!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bd7f-124">[!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]</span></span>  
  
 <span data-ttu-id="2bd7f-125">Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-125">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 <span data-ttu-id="2bd7f-126">[!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bd7f-126">[!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bd7f-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bd7f-127">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2bd7f-128">Description</span><span class="sxs-lookup"><span data-stu-id="2bd7f-128">Description</span></span>  
 <span data-ttu-id="2bd7f-129">Dans l’exemple suivant, un tableau à deux dimensions d’entiers est initialisé et passé à la méthode `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-129">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="2bd7f-130">La méthode affiche les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="2bd7f-130">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2bd7f-131">Code</span><span class="sxs-lookup"><span data-stu-id="2bd7f-131">Code</span></span>  
 <span data-ttu-id="2bd7f-132">[!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bd7f-132">[!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd7f-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bd7f-133">See Also</span></span>  
 <span data-ttu-id="2bd7f-134">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2bd7f-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2bd7f-135">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="2bd7f-135">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="2bd7f-136">[Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="2bd7f-136">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 <span data-ttu-id="2bd7f-137">[Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="2bd7f-137">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="2bd7f-138">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="2bd7f-138">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

