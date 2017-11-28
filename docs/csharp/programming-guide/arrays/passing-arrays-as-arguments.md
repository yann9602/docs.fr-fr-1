---
title: "Passage de tableaux en tant qu’arguments (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f152173b747a171052ab99f261ed91ced9465fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="7de06-102">Passage de tableaux en tant qu’arguments (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="7de06-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="7de06-103">Les tableaux peuvent être passés en tant qu’arguments à des paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="7de06-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="7de06-104">Comme les tableaux sont des types référence, la méthode peut modifier la valeur des éléments.</span><span class="sxs-lookup"><span data-stu-id="7de06-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="7de06-105">Passage de tableaux unidimensionnels en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="7de06-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="7de06-106">Vous pouvez passer un tableau unidimensionnel initialisé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="7de06-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="7de06-107">Par exemple, l’instruction suivante envoie un tableau à une méthode Print.</span><span class="sxs-lookup"><span data-stu-id="7de06-107">For example, the following statement sends an array to a print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 <span data-ttu-id="7de06-108">Le code suivant illustre une implémentation partielle de la méthode Print.</span><span class="sxs-lookup"><span data-stu-id="7de06-108">The following code shows a partial implementation of the print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 <span data-ttu-id="7de06-109">Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7de06-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="7de06-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="7de06-110">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7de06-111">Description</span><span class="sxs-lookup"><span data-stu-id="7de06-111">Description</span></span>  
 <span data-ttu-id="7de06-112">Dans l’exemple suivant, un tableau de chaînes est initialisé et passé en tant qu’argument à une méthode `PrintArray` pour des chaînes.</span><span class="sxs-lookup"><span data-stu-id="7de06-112">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="7de06-113">La méthode affiche les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="7de06-113">The method displays the elements of the array.</span></span> <span data-ttu-id="7de06-114">Ensuite, les méthodes `ChangeArray` et `ChangeArrayElement` sont appelées pour montrer que l’envoi d’un argument de tableau par valeur n’empêche pas les modifications au niveau des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="7de06-114">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7de06-115">Code</span><span class="sxs-lookup"><span data-stu-id="7de06-115">Code</span></span>  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="7de06-116">Passage de tableaux multidimensionnels en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="7de06-116">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="7de06-117">Vous pouvez passer un tableau multidimensionnel initialisé à une méthode de la même manière que vous passez un tableau unidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="7de06-117">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 <span data-ttu-id="7de06-118">Le code suivant illustre une déclaration partielle d’une méthode Print qui accepte un tableau à deux dimensions en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="7de06-118">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 <span data-ttu-id="7de06-119">Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7de06-119">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a><span data-ttu-id="7de06-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="7de06-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7de06-121">Description</span><span class="sxs-lookup"><span data-stu-id="7de06-121">Description</span></span>  
 <span data-ttu-id="7de06-122">Dans l’exemple suivant, un tableau à deux dimensions d’entiers est initialisé et passé à la méthode `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="7de06-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="7de06-123">La méthode affiche les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="7de06-123">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7de06-124">Code</span><span class="sxs-lookup"><span data-stu-id="7de06-124">Code</span></span>  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7de06-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7de06-125">See Also</span></span>  
 [<span data-ttu-id="7de06-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7de06-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7de06-127">Tableaux</span><span class="sxs-lookup"><span data-stu-id="7de06-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="7de06-128">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="7de06-128">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="7de06-129">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="7de06-129">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="7de06-130">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="7de06-130">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
