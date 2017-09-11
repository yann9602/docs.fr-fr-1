---
title: Tableaux (guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: 33
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
ms.openlocfilehash: 1035caae15b64d1311305cfe4c1f1a74c80ed19a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="25d72-102">Tableaux (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="25d72-102">Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="25d72-103">Vous pouvez stocker plusieurs variables du même type dans une structure de données de type tableau.</span><span class="sxs-lookup"><span data-stu-id="25d72-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="25d72-104">Vous déclarez un tableau en spécifiant le type de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="25d72-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="25d72-105">Les exemples suivants créent des tableaux unidimensionnels, multidimensionnels et en escalier :</span><span class="sxs-lookup"><span data-stu-id="25d72-105">The following examples create single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 <span data-ttu-id="25d72-106">[!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="25d72-106">[!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]</span></span>  
  
## <a name="array-overview"></a><span data-ttu-id="25d72-107">Vue d’ensemble du tableau</span><span class="sxs-lookup"><span data-stu-id="25d72-107">Array Overview</span></span>  
 <span data-ttu-id="25d72-108">Un tableau possède les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="25d72-108">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="25d72-109">Un tableau peut être [unidimensionnel](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [multidimensionnel](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) ou [en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="25d72-109">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="25d72-110">Le nombre de dimensions et la longueur de chaque dimension sont établis lors de la création de l’instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="25d72-110">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="25d72-111">Ces valeurs ne peuvent pas être modifiées pendant la durée de vie de l’instance.</span><span class="sxs-lookup"><span data-stu-id="25d72-111">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="25d72-112">Les valeurs par défaut des éléments de tableau numériques sont définies sur zéro et les éléments de référence sont définis sur Null.</span><span class="sxs-lookup"><span data-stu-id="25d72-112">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="25d72-113">Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.</span><span class="sxs-lookup"><span data-stu-id="25d72-113">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="25d72-114">Les tableaux sont indexés sur zéro : un tableau avec `n` éléments est indexée de `0` à `n-1`.</span><span class="sxs-lookup"><span data-stu-id="25d72-114">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="25d72-115">Les éléments de tableau peuvent être de n’importe quel type, y compris un type tableau.</span><span class="sxs-lookup"><span data-stu-id="25d72-115">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="25d72-116">Les types tableau sont des [types référence](../../../csharp/language-reference/keywords/reference-types.md) dérivés du type de base abstrait <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="25d72-116">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="25d72-117">Étant donné que ce type implémente <xref:System.Collections.IEnumerable> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser l’itération [foreach](../../../csharp/language-reference/keywords/foreach-in.md) sur tous les tableaux en C#.</span><span class="sxs-lookup"><span data-stu-id="25d72-117">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="25d72-118">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="25d72-118">Related Sections</span></span>  
  
-   [<span data-ttu-id="25d72-119">Tableaux comme objets</span><span class="sxs-lookup"><span data-stu-id="25d72-119">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="25d72-120">Utilisation de foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="25d72-120">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="25d72-121">Passage de tableaux en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="25d72-121">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [<span data-ttu-id="25d72-122">Passage de tableaux à l’aide de paramètres ref et out</span><span class="sxs-lookup"><span data-stu-id="25d72-122">Passing Arrays Using ref and out</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a><span data-ttu-id="25d72-123">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="25d72-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="25d72-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25d72-124">See Also</span></span>  
 <span data-ttu-id="25d72-125">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="25d72-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="25d72-126">[Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span><span class="sxs-lookup"><span data-stu-id="25d72-126">[Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span></span>  
 [<span data-ttu-id="25d72-127">Type de collection Array</span><span class="sxs-lookup"><span data-stu-id="25d72-127">Array Collection Type</span></span>](http://msdn.microsoft.com/en-us/8a9964de-8941-47b1-a3cf-a01bc88db9e8)

