---
title: 'Comment : initialiser une variable tableau en Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3ccdbed601d3fa87acb0833bc153c199b17a4eba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="d3e59-102">Comment : initialiser une variable tableau en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3e59-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="d3e59-103">Vous initialisez une variable tableau en incluant le littéral dans un `New` clause et en spécifiant les valeurs initiales du tableau.</span><span class="sxs-lookup"><span data-stu-id="d3e59-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="d3e59-104">Vous pouvez spécifier le type ou pouvoir être déduit à partir des valeurs du littéral de tableau.</span><span class="sxs-lookup"><span data-stu-id="d3e59-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="d3e59-105">Pour plus d’informations sur la façon dont le type est déduit, consultez « Remplissage d’un tableau avec des valeurs initiales » dans [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="d3e59-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="d3e59-106">Pour initialiser une variable tableau à l’aide d’un littéral de tableau</span><span class="sxs-lookup"><span data-stu-id="d3e59-106">To initialize an array variable by using an array literal</span></span>  
  
-   <span data-ttu-id="d3e59-107">Dans le `New` clause, ou lorsque vous affectez la valeur de tableau, fournissez les valeurs d’élément à l’intérieur des accolades (`{}`).</span><span class="sxs-lookup"><span data-stu-id="d3e59-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="d3e59-108">L’exemple suivant montre plusieurs façons de déclarer, créer et initialiser une variable pour contenir un tableau qui comporte des éléments de type `Char`.</span><span class="sxs-lookup"><span data-stu-id="d3e59-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     <span data-ttu-id="d3e59-109">Après l’exécution de chaque instruction, le tableau créé a une longueur de 3, avec des éléments à l’index 0 à l’index 2 contenant les valeurs initiales.</span><span class="sxs-lookup"><span data-stu-id="d3e59-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="d3e59-110">Si vous fournissez à la fois la limite supérieure et les valeurs, vous devez inclure une valeur pour chaque élément de l’index 0 jusqu'à la limite supérieure.</span><span class="sxs-lookup"><span data-stu-id="d3e59-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="d3e59-111">Notez que vous n’êtes pas obligé de spécifier la limite supérieure d’index si vous fournissez des valeurs d’éléments dans un littéral de tableau.</span><span class="sxs-lookup"><span data-stu-id="d3e59-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="d3e59-112">Si aucune limite supérieure n’est spécifiée, la taille du tableau est déduite en fonction du nombre de valeurs dans le littéral de tableau.</span><span class="sxs-lookup"><span data-stu-id="d3e59-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="d3e59-113">Pour initialiser une variable de tableau multidimensionnel à l’aide de littéraux de tableau</span><span class="sxs-lookup"><span data-stu-id="d3e59-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
-   <span data-ttu-id="d3e59-114">Imbriquer des valeurs à l’intérieur des accolades (`{}`) entre accolades.</span><span class="sxs-lookup"><span data-stu-id="d3e59-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="d3e59-115">Vérifiez que les littéraux de tableaux imbriqués que tous déduits en tant que tableaux du même type et de longueur.</span><span class="sxs-lookup"><span data-stu-id="d3e59-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="d3e59-116">L’exemple de code suivant montre plusieurs exemples d’initialisation de tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="d3e59-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   <span data-ttu-id="d3e59-117">Vous pouvez explicitement spécifier les limites du tableau, ou les ignorer et indiquer au compilateur de déduire les limites du tableau selon les valeurs du littéral de tableau.</span><span class="sxs-lookup"><span data-stu-id="d3e59-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="d3e59-118">Si vous fournissez à la fois les limites supérieures et les valeurs, vous devez inclure une valeur pour chaque élément de l’index 0 jusqu'à la limite supérieure de chaque dimension.</span><span class="sxs-lookup"><span data-stu-id="d3e59-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="d3e59-119">L’exemple suivant montre plusieurs façons de déclarer, créer et initialiser une variable pour contenir un tableau à deux dimensions qui comporte des éléments de type`Short`</span><span class="sxs-lookup"><span data-stu-id="d3e59-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     <span data-ttu-id="d3e59-120">Après l’exécution de chaque instruction, le tableau créé contient six éléments initialisés qui ont des index `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, et `(1,2)`.</span><span class="sxs-lookup"><span data-stu-id="d3e59-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="d3e59-121">Chaque emplacement de tableau contient la valeur `10`.</span><span class="sxs-lookup"><span data-stu-id="d3e59-121">Each array location contains the value `10`.</span></span>  
  
-   <span data-ttu-id="d3e59-122">L’exemple suivant effectue une itération dans un tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="d3e59-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="d3e59-123">Dans une application de console Windows qui est écrit en Visual Basic, collez le code à l’intérieur de la `Sub Main()` (méthode).</span><span class="sxs-lookup"><span data-stu-id="d3e59-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="d3e59-124">Les commentaires dernière affichent la sortie.</span><span class="sxs-lookup"><span data-stu-id="d3e59-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="d3e59-125">Pour initialiser une variable tableau en escalier à l’aide de littéraux de tableau</span><span class="sxs-lookup"><span data-stu-id="d3e59-125">To initialize a jagged array variable by using array literals</span></span>  
  
-   <span data-ttu-id="d3e59-126">Imbriquer des valeurs de l’objet à l’intérieur des accolades (`{}`).</span><span class="sxs-lookup"><span data-stu-id="d3e59-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="d3e59-127">Bien que vous pouvez également imbriquer des littéraux de tableau qui spécifient des tableaux de longueurs différentes, dans le cas d’un tableau en escalier, assurez-vous que les littéraux de tableaux imbriqués sont placés entre parenthèses (`()`).</span><span class="sxs-lookup"><span data-stu-id="d3e59-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="d3e59-128">Les parenthèses forcent l’évaluation des littéraux de tableaux imbriqués et les tableaux obtenus sont utilisés comme valeurs initiales du tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="d3e59-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="d3e59-129">L’exemple de code suivant montre deux exemples de l’initialisation de tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="d3e59-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   <span data-ttu-id="d3e59-130">L’exemple suivant effectue une itération dans un tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="d3e59-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="d3e59-131">Dans une application de console Windows qui est écrit en Visual Basic, collez le code à l’intérieur de la `Sub Main()` (méthode).</span><span class="sxs-lookup"><span data-stu-id="d3e59-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="d3e59-132">Les dernière commentaires dans le code affichent la sortie.</span><span class="sxs-lookup"><span data-stu-id="d3e59-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d3e59-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3e59-133">See Also</span></span>  
 [<span data-ttu-id="d3e59-134">Tableaux</span><span class="sxs-lookup"><span data-stu-id="d3e59-134">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="d3e59-135">Dépannage des tableaux</span><span class="sxs-lookup"><span data-stu-id="d3e59-135">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
