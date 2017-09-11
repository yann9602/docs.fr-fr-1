---
title: Tableaux en escalier (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
caps.latest.revision: 24
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
ms.openlocfilehash: cb6c0823af37924235dba7daa20e607cb8402a79
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="fc285-102">Tableaux en escalier (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fc285-102">Jagged Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="fc285-103">Un tableau en escalier est un tableau dont les éléments sont des tableaux.</span><span class="sxs-lookup"><span data-stu-id="fc285-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="fc285-104">Les éléments d’un tableau en escalier peuvent être de dimensions et de tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="fc285-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="fc285-105">Un tableau en escalier est parfois appelé « tableau de tableaux ».</span><span class="sxs-lookup"><span data-stu-id="fc285-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="fc285-106">Les exemples suivants montrent comment déclarer, initialiser et accéder aux tableaux en escalier.</span><span class="sxs-lookup"><span data-stu-id="fc285-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="fc285-107">Voici une déclaration d’un tableau unidimensionnel qui comporte trois éléments, chacun d’eux étant un tableau unidimensionnel d’entiers :</span><span class="sxs-lookup"><span data-stu-id="fc285-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 <span data-ttu-id="fc285-108">[!code-cs[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-108">[!code-cs[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="fc285-109">Pour pouvoir utiliser `jaggedArray`, vous devez initialiser ses éléments.</span><span class="sxs-lookup"><span data-stu-id="fc285-109">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="fc285-110">Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fc285-110">You can initialize the elements like this:</span></span>  
  
 <span data-ttu-id="fc285-111">[!code-cs[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-111">[!code-cs[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]</span></span>  
  
 <span data-ttu-id="fc285-112">Chacun des éléments est un tableau unidimensionnel d’entiers.</span><span class="sxs-lookup"><span data-stu-id="fc285-112">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="fc285-113">Le premier élément est un tableau de 5 entiers, le deuxième est un tableau de 4 entiers et le troisième est un tableau de 2 entiers.</span><span class="sxs-lookup"><span data-stu-id="fc285-113">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="fc285-114">Il est aussi possible d’utiliser des initialiseurs pour remplir les éléments de tableau de valeurs, auquel cas vous n’avez pas besoin de la taille du tableau.</span><span class="sxs-lookup"><span data-stu-id="fc285-114">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="fc285-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="fc285-115">For example:</span></span>  
  
 <span data-ttu-id="fc285-116">[!code-cs[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-116">[!code-cs[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]</span></span>  
  
 <span data-ttu-id="fc285-117">Vous pouvez aussi initialiser le tableau au moment de la déclaration, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="fc285-117">You can also initialize the array upon declaration like this:</span></span>  
  
 <span data-ttu-id="fc285-118">[!code-cs[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-118">[!code-cs[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]</span></span>  
  
 <span data-ttu-id="fc285-119">Vous pouvez utiliser la forme abrégée suivante.</span><span class="sxs-lookup"><span data-stu-id="fc285-119">You can use the following shorthand form.</span></span> <span data-ttu-id="fc285-120">Notez que vous ne pouvez pas omettre l’opérateur `new` dans l’initialisation des éléments, car il n’existe pas d’initialisation par défaut pour les éléments :</span><span class="sxs-lookup"><span data-stu-id="fc285-120">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 <span data-ttu-id="fc285-121">[!code-cs[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-121">[!code-cs[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]</span></span>  
  
 <span data-ttu-id="fc285-122">Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.</span><span class="sxs-lookup"><span data-stu-id="fc285-122">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="fc285-123">Vous pouvez accéder aux éléments de tableau individuels comme dans ces exemples :</span><span class="sxs-lookup"><span data-stu-id="fc285-123">You can access individual array elements like these examples:</span></span>  
  
 <span data-ttu-id="fc285-124">[!code-cs[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-124">[!code-cs[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]</span></span>  
  
 <span data-ttu-id="fc285-125">Il est possible de combiner des tableaux en escalier et des tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="fc285-125">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="fc285-126">Vous trouverez ci-dessous une déclaration et une initialisation d’un tableau en escalier unidimensionnel composé de trois éléments de tableau à deux dimensions de tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="fc285-126">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="fc285-127">Pour plus d’informations sur les tableaux à deux dimensions, consultez [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="fc285-127">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 <span data-ttu-id="fc285-128">[!code-cs[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-128">[!code-cs[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]</span></span>  
  
 <span data-ttu-id="fc285-129">Vous pouvez accéder aux différents éléments comme le montre cet exemple, qui présente la valeur de l’élément `[1,0]` du premier tableau (valeur `5`) :</span><span class="sxs-lookup"><span data-stu-id="fc285-129">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 <span data-ttu-id="fc285-130">[!code-cs[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-130">[!code-cs[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]</span></span>  
  
 <span data-ttu-id="fc285-131">La méthode `Length` retourne le nombre de tableaux contenus dans le tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="fc285-131">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="fc285-132">Par exemple, en supposant que vous avez déclaré le tableau précédent, cette ligne :</span><span class="sxs-lookup"><span data-stu-id="fc285-132">For example, assuming you have declared the previous array, this line:</span></span>  
  
 <span data-ttu-id="fc285-133">[!code-cs[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-133">[!code-cs[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]</span></span>  
  
 <span data-ttu-id="fc285-134">retourne la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="fc285-134">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc285-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="fc285-135">Example</span></span>  
 <span data-ttu-id="fc285-136">Cet exemple génère un tableau dont les éléments sont eux-mêmes des tableaux.</span><span class="sxs-lookup"><span data-stu-id="fc285-136">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="fc285-137">Chacun des éléments de tableau ont une taille différente.</span><span class="sxs-lookup"><span data-stu-id="fc285-137">Each one of the array elements has a different size.</span></span>  
  
 <span data-ttu-id="fc285-138">[!code-cs[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="fc285-138">[!code-cs[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc285-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc285-139">See Also</span></span>  
 <span data-ttu-id="fc285-140"><xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="fc285-140"><xref:System.Array></span></span>   
 <span data-ttu-id="fc285-141">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fc285-141">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="fc285-142">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="fc285-142">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="fc285-143">[Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="fc285-143">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 [<span data-ttu-id="fc285-144">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="fc285-144">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)

