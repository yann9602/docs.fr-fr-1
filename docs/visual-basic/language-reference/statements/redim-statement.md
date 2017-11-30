---
title: ReDim, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cec66ee33bfd82b3abd623a0130f5635aa3d1d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="ec2fc-102">ReDim, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec2fc-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="ec2fc-103">Réalloue l'espace de stockage d'une variable tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec2fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec2fc-104">Syntax</span></span>  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ec2fc-105">Composants</span><span class="sxs-lookup"><span data-stu-id="ec2fc-105">Parts</span></span>  
  
|<span data-ttu-id="ec2fc-106">Terme</span><span class="sxs-lookup"><span data-stu-id="ec2fc-106">Term</span></span>|<span data-ttu-id="ec2fc-107">Définition</span><span class="sxs-lookup"><span data-stu-id="ec2fc-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="ec2fc-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-108">Optional.</span></span> <span data-ttu-id="ec2fc-109">Modificateur utilisé pour conserver les données du tableau existant quand vous modifiez la taille de la dernière dimension uniquement.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="ec2fc-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-110">Required.</span></span> <span data-ttu-id="ec2fc-111">Nom de la variable de tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-111">Name of the array variable.</span></span> <span data-ttu-id="ec2fc-112">Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ec2fc-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="ec2fc-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-113">Required.</span></span> <span data-ttu-id="ec2fc-114">Liste des limites de chaque dimension du tableau redéfini.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec2fc-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="ec2fc-115">Remarks</span></span>  
 <span data-ttu-id="ec2fc-116">Vous pouvez utiliser l'instruction `ReDim` pour modifier la taille d'une ou plusieurs dimensions d'un tableau qui a déjà été déclaré.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="ec2fc-117">Si vous possédez un grand tableau et que vous n'avez plus besoin de certains de ses éléments, `ReDim` peut libérer de la mémoire en réduisant la taille du tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="ec2fc-118">En revanche, si votre tableau a besoin d'éléments supplémentaires, `ReDim` peut les ajouter.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="ec2fc-119">L'instruction `ReDim` est destinée uniquement aux tableaux.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="ec2fc-120">Il n'est pas valide sur les scalaires (variables contenant une seule valeur), les collections ou les structures.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="ec2fc-121">Notez que si vous déclarez une variable de type `Array`, l'instruction `ReDim` ne dispose pas d'informations de type suffisantes pour créer le tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="ec2fc-122">Vous pouvez utiliser `ReDim` uniquement au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="ec2fc-123">Par conséquent, le contexte de déclaration pour la variable doit être une procédure ; il ne peut pas être un fichier source, un espace de noms, une interface, une classe, une structure, un module ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="ec2fc-124">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ec2fc-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ec2fc-125">Règles</span><span class="sxs-lookup"><span data-stu-id="ec2fc-125">Rules</span></span>  
  
-   <span data-ttu-id="ec2fc-126">**Plusieurs Variables.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-126">**Multiple Variables.**</span></span> <span data-ttu-id="ec2fc-127">Vous pouvez redimensionner plusieurs variables tableau dans la même instruction de déclaration et spécifier les parties `name` et `boundlist` pour chaque variable.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="ec2fc-128">Les variables multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-128">Multiple variables are separated by commas.</span></span>  
  
-   <span data-ttu-id="ec2fc-129">**Limites de tableau.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-129">**Array Bounds.**</span></span> <span data-ttu-id="ec2fc-130">Chaque entrée dans `boundlist` peut spécifier les limites inférieures et supérieures de cette dimension.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="ec2fc-131">La limite inférieure est toujours 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="ec2fc-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="ec2fc-132">La limite supérieure est la valeur d'index la plus élevée possible pour cette dimension, pas la longueur de la dimension (qui est la limite supérieure plus un).</span><span class="sxs-lookup"><span data-stu-id="ec2fc-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="ec2fc-133">L'index pour chaque dimension varie de 0 à sa valeur liée supérieure.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="ec2fc-134">Le nombre de dimensions dans `boundlist` doit correspondre au nombre de dimensions (rang) d'origine du tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
-   <span data-ttu-id="ec2fc-135">**Types de données.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-135">**Data Types.**</span></span> <span data-ttu-id="ec2fc-136">L'instruction `ReDim` ne peut pas modifier le type de données d'une variable tableau ou de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
-   <span data-ttu-id="ec2fc-137">**Initialisation.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-137">**Initialization.**</span></span> <span data-ttu-id="ec2fc-138">L'instruction `ReDim` ne peut pas fournir de nouvelles valeurs d'initialisation pour les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
-   <span data-ttu-id="ec2fc-139">**Rang.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-139">**Rank.**</span></span> <span data-ttu-id="ec2fc-140">L'instruction `ReDim` ne peut pas modifier le rang (nombre de dimensions) du tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
-   <span data-ttu-id="ec2fc-141">**Redimensionnement avec Preserve.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="ec2fc-142">Si vous utilisez `Preserve`, vous pouvez uniquement redimensionner la dernière dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="ec2fc-143">Pour chaque autre dimension, vous devez spécifier la limite du tableau existant.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="ec2fc-144">Par exemple, si votre tableau ne comporte qu'une seule dimension, vous pouvez la redimensionner tout en conservant le contenu du tableau, car vous modifiez la dernière et seule dimension.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="ec2fc-145">Toutefois, si votre tableau comporte deux dimensions ou plus, vous pouvez modifier la taille de la dernière dimension seulement si vous utilisez `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
-   <span data-ttu-id="ec2fc-146">**Propriétés.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-146">**Properties.**</span></span> <span data-ttu-id="ec2fc-147">Vous pouvez utiliser `ReDim` sur une propriété qui contient un tableau de valeurs.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="ec2fc-148">Comportement</span><span class="sxs-lookup"><span data-stu-id="ec2fc-148">Behavior</span></span>  
  
-   <span data-ttu-id="ec2fc-149">**Remplacement de tableau.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-149">**Array Replacement.**</span></span> <span data-ttu-id="ec2fc-150">`ReDim`Libère le tableau existant et crée un nouveau tableau avec le même rang.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="ec2fc-151">Le nouveau tableau remplace le tableau libéré dans la variable tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-151">The new array replaces the released array in the array variable.</span></span>  
  
-   <span data-ttu-id="ec2fc-152">**Initialisation sans Preserve.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="ec2fc-153">Si vous ne spécifiez pas `Preserve`, `ReDim` initialise les éléments du nouveau tableau à l'aide de la valeur par défaut de leur type de données.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
-   <span data-ttu-id="ec2fc-154">**Initialisation avec Preserve.**</span><span class="sxs-lookup"><span data-stu-id="ec2fc-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="ec2fc-155">Si vous spécifiez `Preserve`, Visual Basic copie les éléments du tableau existant dans le nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec2fc-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="ec2fc-156">Example</span></span>  
 <span data-ttu-id="ec2fc-157">L'exemple suivant augmente la taille de la dernière dimension d'un tableau dynamique sans perte de données existantes dans le tableau, puis réduit la taille avec une perte de données partielle.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="ec2fc-158">Enfin, il réduit la taille à sa valeur d'origine et réinitialise tous les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 <span data-ttu-id="ec2fc-159">L'instruction `Dim` crée un tableau à trois dimensions.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="ec2fc-160">Étant donné que chaque dimension est déclarée avec une limite de 10, l'index de tableau pour chaque dimension peut aller de 0 à 10.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="ec2fc-161">Dans la discussion suivante, les trois dimensions sont appelées « couche », « ligne » et « colonne ».</span><span class="sxs-lookup"><span data-stu-id="ec2fc-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="ec2fc-162">La première instruction `ReDim` crée un tableau qui remplace le tableau existant dans la variable `intArray`.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="ec2fc-163">`ReDim` copie tous les éléments du tableau existant dans le nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="ec2fc-164">Elle ajoute également 10 colonnes supplémentaires à la fin de chaque ligne dans chaque couche et initialise les éléments de ces nouvelles colonnes à 0 (la valeur par défaut d'`Integer`, qui est le type d'élément du tableau).</span><span class="sxs-lookup"><span data-stu-id="ec2fc-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="ec2fc-165">La deuxième instruction `ReDim` crée un autre tableau et copie tous les éléments adaptés.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="ec2fc-166">Toutefois, les cinq colonnes sont perdus à la fin de chaque ligne dans chaque couche.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="ec2fc-167">Cela n'est pas un problème si vous avez fini d'utiliser ces colonnes.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="ec2fc-168">La réduction de la taille d'un grand tableau peut libérer de la mémoire dont vous n'avez plus besoin.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="ec2fc-169">La troisième instruction `ReDim` crée un autre tableau et supprime cinq autres colonnes de la fin de chaque ligne dans chaque couche.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="ec2fc-170">Cette fois-ci, elle ne copie pas les éléments existants.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="ec2fc-171">Cette instruction rétablit la taille d'origine du tableau.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="ec2fc-172">Étant donné que l'instruction n'inclut pas le modificateur `Preserve`, elle définit tous les éléments de tableau à leurs valeurs par défaut d'origine.</span><span class="sxs-lookup"><span data-stu-id="ec2fc-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="ec2fc-173">Pour obtenir des exemples supplémentaires, consultez [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="ec2fc-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2fc-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec2fc-174">See Also</span></span>  
 <xref:System.IndexOutOfRangeException>  
 [<span data-ttu-id="ec2fc-175">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="ec2fc-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="ec2fc-176">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="ec2fc-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="ec2fc-177">Erase (instruction)</span><span class="sxs-lookup"><span data-stu-id="ec2fc-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [<span data-ttu-id="ec2fc-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="ec2fc-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="ec2fc-179">Tableaux</span><span class="sxs-lookup"><span data-stu-id="ec2fc-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
