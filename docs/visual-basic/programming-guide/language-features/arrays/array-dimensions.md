---
title: Dimensions du tableau dans Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21e170ca5942862a26e05428fffaea7d1e875e19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="4170a-102">Dimensions du tableau dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4170a-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="4170a-103">A *dimension* est une direction dans laquelle vous pouvez varier la spécification des éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4170a-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="4170a-104">Un tableau qui contient les ventes totales pour chaque jour du mois possède une dimension (le jour du mois).</span><span class="sxs-lookup"><span data-stu-id="4170a-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="4170a-105">Un tableau qui contient les ventes totales par service pour chaque jour du mois possède deux dimensions (le numéro de service et le jour du mois).</span><span class="sxs-lookup"><span data-stu-id="4170a-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="4170a-106">Le nombre de dimensions dispose d’un tableau est appelé son *rang*.</span><span class="sxs-lookup"><span data-stu-id="4170a-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4170a-107">Vous pouvez utiliser le <xref:System.Array.Rank%2A> propriété pour déterminer le nombre de dimensions d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4170a-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="4170a-108">Utilisation des Dimensions</span><span class="sxs-lookup"><span data-stu-id="4170a-108">Working with Dimensions</span></span>  
 <span data-ttu-id="4170a-109">Vous spécifiez un élément d’un tableau en fournissant un *index* ou *indice* pour chacune de ses dimensions.</span><span class="sxs-lookup"><span data-stu-id="4170a-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="4170a-110">Les éléments sont contigus pour chaque dimension de l’index 0 dans l’index le plus élevé pour cette dimension.</span><span class="sxs-lookup"><span data-stu-id="4170a-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="4170a-111">Les illustrations suivantes montrent la structure conceptuelle de tableaux avec des classements différents.</span><span class="sxs-lookup"><span data-stu-id="4170a-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="4170a-112">Chaque élément dans les illustrations affiche les valeurs d’index qui y accéder.</span><span class="sxs-lookup"><span data-stu-id="4170a-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="4170a-113">Par exemple, vous pouvez accéder le premier élément de la deuxième ligne du tableau à deux dimensions en spécifiant les index `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="4170a-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="4170a-114">![Diagramme graphique d’un &#45; tableau unidimensionnel](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="4170a-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="4170a-115">Tableau unidimensionnel</span><span class="sxs-lookup"><span data-stu-id="4170a-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="4170a-116">![Diagramme graphique de deux &#45; tableau unidimensionnel](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="4170a-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="4170a-117">Tableau à deux dimensions</span><span class="sxs-lookup"><span data-stu-id="4170a-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="4170a-118">![Diagramme graphique de trois &#45; tableau unidimensionnel](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="4170a-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="4170a-119">Tableau à trois dimensions</span><span class="sxs-lookup"><span data-stu-id="4170a-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="4170a-120">Une Dimension</span><span class="sxs-lookup"><span data-stu-id="4170a-120">One Dimension</span></span>  
 <span data-ttu-id="4170a-121">De nombreux groupes ont une seule dimension, telles que le nombre de personnes pour chaque âge.</span><span class="sxs-lookup"><span data-stu-id="4170a-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="4170a-122">La seule exigence pour spécifier un élément est la durée de vie pour laquelle cet élément conserve le nombre.</span><span class="sxs-lookup"><span data-stu-id="4170a-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="4170a-123">Par conséquent, ce type de tableau utilise un seul index.</span><span class="sxs-lookup"><span data-stu-id="4170a-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="4170a-124">L’exemple suivant déclare une variable qui doit contenir un *tableau unidimensionnel* d’âge du nombre d’âgés de 0 à 120.</span><span class="sxs-lookup"><span data-stu-id="4170a-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="4170a-125">Deux Dimensions</span><span class="sxs-lookup"><span data-stu-id="4170a-125">Two Dimensions</span></span>  
 <span data-ttu-id="4170a-126">Certains tableaux ont deux dimensions, telles que le nombre de bureaux à chaque étage de chaque génération sur un site.</span><span class="sxs-lookup"><span data-stu-id="4170a-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="4170a-127">La spécification d’un élément requiert à la fois le numéro du bâtiment et l’étage, et chaque élément possède le compte pour cette combinaison de bâtiment et étage.</span><span class="sxs-lookup"><span data-stu-id="4170a-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="4170a-128">Par conséquent, ce type de tableau utilise deux index.</span><span class="sxs-lookup"><span data-stu-id="4170a-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="4170a-129">L’exemple suivant déclare une variable qui doit contenir un *tableau à deux dimensions* de comptes de bureau, pour les bâtiments 0 à 40 et planchers 0 à 5.</span><span class="sxs-lookup"><span data-stu-id="4170a-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="4170a-130">Un tableau à deux dimensions est également appelé un *tableau rectangulaire*.</span><span class="sxs-lookup"><span data-stu-id="4170a-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="4170a-131">Trois Dimensions</span><span class="sxs-lookup"><span data-stu-id="4170a-131">Three Dimensions</span></span>  
 <span data-ttu-id="4170a-132">Certains tableaux ont trois dimensions, telles que les valeurs dans l’espace à trois dimensions.</span><span class="sxs-lookup"><span data-stu-id="4170a-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="4170a-133">Ce type de tableau utilise trois index, qui dans ce cas représentent le x, y et les coordonnées z de l’espace physique.</span><span class="sxs-lookup"><span data-stu-id="4170a-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="4170a-134">L’exemple suivant déclare une variable qui doit contenir un *tableau tridimensionnel* de température à différents points dans un volume en trois dimensions.</span><span class="sxs-lookup"><span data-stu-id="4170a-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="4170a-135">Plus de trois Dimensions</span><span class="sxs-lookup"><span data-stu-id="4170a-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="4170a-136">Un tableau peut avoir jusqu'à 32 dimensions, mais il est rare d’avoir plus de trois.</span><span class="sxs-lookup"><span data-stu-id="4170a-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4170a-137">Lorsque vous ajoutez des dimensions à un tableau, le stockage total nécessaire pour le tableau augmente considérablement, c’est le cas des tableaux multidimensionnels utiliser avec précaution.</span><span class="sxs-lookup"><span data-stu-id="4170a-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="4170a-138">À l’aide de différentes Dimensions</span><span class="sxs-lookup"><span data-stu-id="4170a-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="4170a-139">Supposons que vous souhaitez effectuer le suivi des montants des ventes pour tous les jours du mois en cours.</span><span class="sxs-lookup"><span data-stu-id="4170a-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="4170a-140">Vous pouvez déclarer un tableau unidimensionnel avec 31 éléments, un pour chaque jour du mois, comme l’exemple suivant montre.</span><span class="sxs-lookup"><span data-stu-id="4170a-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="4170a-141">Maintenant Supposons que vous souhaitez suivre les mêmes informations non seulement pour tous les jours du mois, mais également pour chaque mois de l’année.</span><span class="sxs-lookup"><span data-stu-id="4170a-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="4170a-142">Vous pouvez déclarer un tableau à deux dimensions avec 12 lignes (pour les mois) et 31 colonnes (pour les jours), comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4170a-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="4170a-143">Supposons que vous voulez que votre tableau contiennent à présent des informations pour plusieurs années.</span><span class="sxs-lookup"><span data-stu-id="4170a-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="4170a-144">Si vous souhaitez effectuer le suivi des montants des ventes pendant 5 ans, vous pouviez déclarer un tableau tridimensionnel avec 5 couches, de 12 lignes et de 31 colonnes, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4170a-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="4170a-145">Notez que, étant donné que chaque index varie de 0 à sa valeur maximale, chaque dimension du `salesAmounts` est déclaré comme un de moins que la longueur requise pour cette dimension.</span><span class="sxs-lookup"><span data-stu-id="4170a-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="4170a-146">Notez également que la taille du tableau augmente avec chaque nouvelle dimension.</span><span class="sxs-lookup"><span data-stu-id="4170a-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="4170a-147">Les trois tailles dans les exemples précédents sont respectivement 31, 372 et 1 860 éléments.</span><span class="sxs-lookup"><span data-stu-id="4170a-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4170a-148">Vous pouvez créer un tableau sans utiliser le `Dim` instruction ou `New` clause.</span><span class="sxs-lookup"><span data-stu-id="4170a-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="4170a-149">Par exemple, vous pouvez appeler la <xref:System.Array.CreateInstance%2A> méthode ou un autre composant peut passer à votre code un tableau créé de cette manière.</span><span class="sxs-lookup"><span data-stu-id="4170a-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="4170a-150">Ce type de tableau peut avoir une limite inférieure différente de 0.</span><span class="sxs-lookup"><span data-stu-id="4170a-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="4170a-151">Vous pouvez toujours tester la limite inférieure d’une dimension à l’aide de la <xref:System.Array.GetLowerBound%2A> méthode ou la `LBound` (fonction).</span><span class="sxs-lookup"><span data-stu-id="4170a-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4170a-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4170a-152">See Also</span></span>  
 [<span data-ttu-id="4170a-153">Tableaux</span><span class="sxs-lookup"><span data-stu-id="4170a-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="4170a-154">Dépannage des tableaux</span><span class="sxs-lookup"><span data-stu-id="4170a-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
