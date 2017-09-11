---
title: Tableaux unidimensionnels (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
caps.latest.revision: 18
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
ms.openlocfilehash: cc42640715274b89c4c4a12ced8c0ae6af603318
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="e22b0-102">Tableaux unidimensionnels (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e22b0-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="e22b0-103">Vous pouvez déclarer un tableau unidimensionnel de cinq entiers comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e22b0-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 <span data-ttu-id="e22b0-104">[!code-cs[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e22b0-104">[!code-cs[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="e22b0-105">Ce tableau contient les éléments de `array[0]` à `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="e22b0-105">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="e22b0-106">L’opérateur [new](../../../csharp/language-reference/keywords/new.md) est utilisé pour créer le tableau et initialiser ses éléments à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="e22b0-106">The [new](../../../csharp/language-reference/keywords/new.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="e22b0-107">Dans cet exemple, tous les éléments du tableau sont initialisés à zéro.</span><span class="sxs-lookup"><span data-stu-id="e22b0-107">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="e22b0-108">Un tableau qui stocke des éléments de type chaîne peut être déclaré de la même façon.</span><span class="sxs-lookup"><span data-stu-id="e22b0-108">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="e22b0-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e22b0-109">For example:</span></span>  
  
 <span data-ttu-id="e22b0-110">[!code-cs[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e22b0-110">[!code-cs[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]</span></span>  
  
## <a name="array-initialization"></a><span data-ttu-id="e22b0-111">Initialisation du tableau</span><span class="sxs-lookup"><span data-stu-id="e22b0-111">Array Initialization</span></span>  
 <span data-ttu-id="e22b0-112">Il est possible d’initialiser un tableau lors de sa déclaration, auquel cas le spécificateur de rang n’est pas nécessaire, car il est déjà fourni par le nombre d’éléments figurant dans la liste d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="e22b0-112">It is possible to initialize an array upon declaration, in which case, the rank specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="e22b0-113">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e22b0-113">For example:</span></span>  
  
 <span data-ttu-id="e22b0-114">[!code-cs[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="e22b0-114">[!code-cs[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]</span></span>  
  
 <span data-ttu-id="e22b0-115">Un tableau de chaînes peut être initialisé de la même manière.</span><span class="sxs-lookup"><span data-stu-id="e22b0-115">A string array can be initialized in the same way.</span></span> <span data-ttu-id="e22b0-116">Voici une déclaration d’un tableau de chaînes où chaque élément du tableau est initialisé par un nom de jour de la semaine :</span><span class="sxs-lookup"><span data-stu-id="e22b0-116">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
  
 <span data-ttu-id="e22b0-117">[!code-cs[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="e22b0-117">[!code-cs[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]</span></span>  
  
 <span data-ttu-id="e22b0-118">Quand vous initialisez un tableau lors de sa déclaration, vous pouvez utiliser les raccourcis suivants :</span><span class="sxs-lookup"><span data-stu-id="e22b0-118">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 <span data-ttu-id="e22b0-119">[!code-cs[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="e22b0-119">[!code-cs[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]</span></span>  
  
 <span data-ttu-id="e22b0-120">Il est possible de déclarer une variable de tableau sans initialisation, mais vous devez alors utiliser l’opérateur `new` quand vous affectez un tableau à cette variable.</span><span class="sxs-lookup"><span data-stu-id="e22b0-120">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="e22b0-121">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e22b0-121">For example:</span></span>  
  
 <span data-ttu-id="e22b0-122">[!code-cs[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="e22b0-122">[!code-cs[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]</span></span>  
  
 <span data-ttu-id="e22b0-123">C# 3.0 introduit les tableaux implicitement typés.</span><span class="sxs-lookup"><span data-stu-id="e22b0-123">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="e22b0-124">Pour plus d’informations, consultez [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="e22b0-124">For more information, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="e22b0-125">Tableaux de types valeur et de types référence</span><span class="sxs-lookup"><span data-stu-id="e22b0-125">Value Type and Reference Type Arrays</span></span>  
 <span data-ttu-id="e22b0-126">Considérons la déclaration de tableau suivante :</span><span class="sxs-lookup"><span data-stu-id="e22b0-126">Consider the following array declaration:</span></span>  
  
 <span data-ttu-id="e22b0-127">[!code-cs[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="e22b0-127">[!code-cs[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]</span></span>  
  
 <span data-ttu-id="e22b0-128">Le résultat de cette instruction varie selon que `SomeType` est un type valeur ou un type référence.</span><span class="sxs-lookup"><span data-stu-id="e22b0-128">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="e22b0-129">S’il s’agit d’un type de valeur, l’instruction crée un tableau de 10 éléments, chacun ayant le type `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="e22b0-129">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="e22b0-130">Si `SomeType` est un type référence, l’instruction crée un tableau de 10 éléments dont chacun est initialisé avec une référence null.</span><span class="sxs-lookup"><span data-stu-id="e22b0-130">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="e22b0-131">Pour plus d’informations sur les types valeur et les types références, consultez [Types](../../../csharp/language-reference/keywords/types.md).</span><span class="sxs-lookup"><span data-stu-id="e22b0-131">For more information about value types and reference types, see [Types](../../../csharp/language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e22b0-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e22b0-132">See Also</span></span>  
 <span data-ttu-id="e22b0-133"><xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="e22b0-133"><xref:System.Array></span></span>   
 <span data-ttu-id="e22b0-134">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e22b0-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e22b0-135">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="e22b0-135">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="e22b0-136">[Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="e22b0-136">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="e22b0-137">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="e22b0-137">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

