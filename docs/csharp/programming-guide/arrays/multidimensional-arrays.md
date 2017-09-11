---
title: Tableaux multidimensionnels (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
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
ms.openlocfilehash: 0203046e2038e97cf791141f6863fd8940b22ea4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="437d4-102">Tableaux multidimensionnels (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="437d4-102">Multidimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="437d4-103">Les tableaux peuvent avoir plusieurs dimensions.</span><span class="sxs-lookup"><span data-stu-id="437d4-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="437d4-104">Par exemple, la déclaration suivante crée un tableau à deux dimensions composé de quatre lignes et deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="437d4-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 <span data-ttu-id="437d4-105">[!code-cs[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="437d4-105">[!code-cs[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="437d4-106">La déclaration suivante crée un tableau de trois dimensions, 4, 2 et 3.</span><span class="sxs-lookup"><span data-stu-id="437d4-106">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 <span data-ttu-id="437d4-107">[!code-cs[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="437d4-107">[!code-cs[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]</span></span>  
  
## <a name="array-initialization"></a><span data-ttu-id="437d4-108">Initialisation du tableau</span><span class="sxs-lookup"><span data-stu-id="437d4-108">Array Initialization</span></span>  
 <span data-ttu-id="437d4-109">Vous pouvez initialiser le tableau au moment de la déclaration, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="437d4-109">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 <span data-ttu-id="437d4-110">[!code-cs[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="437d4-110">[!code-cs[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]</span></span>  
  
 <span data-ttu-id="437d4-111">Vous pouvez aussi initialiser le tableau sans spécifier de rang.</span><span class="sxs-lookup"><span data-stu-id="437d4-111">You also can initialize the array without specifying the rank.</span></span>  
  
 <span data-ttu-id="437d4-112">[!code-cs[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="437d4-112">[!code-cs[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]</span></span>  
  
 <span data-ttu-id="437d4-113">Si vous choisissez de déclarer une variable de tableau sans initialisation, vous devez utiliser l’opérateur `new` pour assigner un tableau à la variable.</span><span class="sxs-lookup"><span data-stu-id="437d4-113">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="437d4-114">L’utilisation de `new` est illustrée dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="437d4-114">The use of `new` is shown in the following example.</span></span>  
  
 <span data-ttu-id="437d4-115">[!code-cs[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="437d4-115">[!code-cs[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]</span></span>  
  
 <span data-ttu-id="437d4-116">L’exemple suivant assigne une valeur à un élément de tableau particulier.</span><span class="sxs-lookup"><span data-stu-id="437d4-116">The following example assigns a value to a particular array element.</span></span>  
  
 <span data-ttu-id="437d4-117">[!code-cs[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="437d4-117">[!code-cs[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]</span></span>  
  
 <span data-ttu-id="437d4-118">De la même manière, l’exemple suivant obtient la valeur d’un élément de tableau particulier et l’affecte à la variable `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="437d4-118">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 <span data-ttu-id="437d4-119">[!code-cs[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="437d4-119">[!code-cs[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]</span></span>  
  
 <span data-ttu-id="437d4-120">L’exemple de code suivant initialise les éléments de tableau avec les valeurs par défaut (sauf pour les tableaux en escalier).</span><span class="sxs-lookup"><span data-stu-id="437d4-120">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 <span data-ttu-id="437d4-121">[!code-cs[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="437d4-121">[!code-cs[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437d4-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="437d4-122">See Also</span></span>  
 <span data-ttu-id="437d4-123">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="437d4-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="437d4-124">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="437d4-124">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="437d4-125">[Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="437d4-125">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 [<span data-ttu-id="437d4-126">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="437d4-126">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

