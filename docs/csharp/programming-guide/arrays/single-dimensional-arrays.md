---
title: Tableaux unidimensionnels (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fed9042ba37164927bb8073bc669fafeb5d40598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="1461f-102">Tableaux unidimensionnels (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1461f-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="1461f-103">Vous pouvez déclarer un tableau unidimensionnel de cinq entiers comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1461f-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 <span data-ttu-id="1461f-104">Ce tableau contient les éléments de `array[0]` à `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="1461f-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="1461f-105">L’opérateur [new](../../../csharp/language-reference/keywords/new.md) est utilisé pour créer le tableau et initialiser ses éléments à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="1461f-105">The [new](../../../csharp/language-reference/keywords/new.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="1461f-106">Dans cet exemple, tous les éléments du tableau sont initialisés à zéro.</span><span class="sxs-lookup"><span data-stu-id="1461f-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="1461f-107">Un tableau qui stocke des éléments de type chaîne peut être déclaré de la même façon.</span><span class="sxs-lookup"><span data-stu-id="1461f-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="1461f-108">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1461f-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="1461f-109">Initialisation du tableau</span><span class="sxs-lookup"><span data-stu-id="1461f-109">Array Initialization</span></span>  
 <span data-ttu-id="1461f-110">Il est possible d’initialiser un tableau lors de sa déclaration, auquel cas le spécificateur de rang n’est pas nécessaire, car il est déjà fourni par le nombre d’éléments figurant dans la liste d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="1461f-110">It is possible to initialize an array upon declaration, in which case, the rank specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="1461f-111">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1461f-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 <span data-ttu-id="1461f-112">Un tableau de chaînes peut être initialisé de la même manière.</span><span class="sxs-lookup"><span data-stu-id="1461f-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="1461f-113">Voici une déclaration d’un tableau de chaînes où chaque élément du tableau est initialisé par un nom de jour de la semaine :</span><span class="sxs-lookup"><span data-stu-id="1461f-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 <span data-ttu-id="1461f-114">Quand vous initialisez un tableau lors de sa déclaration, vous pouvez utiliser les raccourcis suivants :</span><span class="sxs-lookup"><span data-stu-id="1461f-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 <span data-ttu-id="1461f-115">Il est possible de déclarer une variable de tableau sans initialisation, mais vous devez alors utiliser l’opérateur `new` quand vous affectez un tableau à cette variable.</span><span class="sxs-lookup"><span data-stu-id="1461f-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="1461f-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1461f-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 <span data-ttu-id="1461f-117">C# 3.0 introduit les tableaux implicitement typés.</span><span class="sxs-lookup"><span data-stu-id="1461f-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="1461f-118">Pour plus d’informations, consultez [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="1461f-118">For more information, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="1461f-119">Tableaux de types valeur et de types référence</span><span class="sxs-lookup"><span data-stu-id="1461f-119">Value Type and Reference Type Arrays</span></span>  
 <span data-ttu-id="1461f-120">Considérons la déclaration de tableau suivante :</span><span class="sxs-lookup"><span data-stu-id="1461f-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 <span data-ttu-id="1461f-121">Le résultat de cette instruction varie selon que `SomeType` est un type valeur ou un type référence.</span><span class="sxs-lookup"><span data-stu-id="1461f-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="1461f-122">S’il s’agit d’un type de valeur, l’instruction crée un tableau de 10 éléments, chacun ayant le type `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="1461f-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="1461f-123">Si `SomeType` est un type référence, l’instruction crée un tableau de 10 éléments dont chacun est initialisé avec une référence null.</span><span class="sxs-lookup"><span data-stu-id="1461f-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="1461f-124">Pour plus d’informations sur les types valeur et les types références, consultez [Types](../../../csharp/language-reference/keywords/types.md).</span><span class="sxs-lookup"><span data-stu-id="1461f-124">For more information about value types and reference types, see [Types](../../../csharp/language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1461f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1461f-125">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="1461f-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1461f-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1461f-127">Tableaux</span><span class="sxs-lookup"><span data-stu-id="1461f-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="1461f-128">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="1461f-128">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="1461f-129">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="1461f-129">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
