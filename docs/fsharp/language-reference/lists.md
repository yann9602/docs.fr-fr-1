---
title: Listes (F#)
description: "En savoir plus sur les listes de F #, une série chronologique, immuable d’éléments du même type."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a1a6075f-064d-4aee-8222-2b59ff16cc12
ms.openlocfilehash: 5802a5a1c48ad05c1765c4c0fa2e8a81a92dee8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="lists"></a><span data-ttu-id="93c65-104">Listes</span><span class="sxs-lookup"><span data-stu-id="93c65-104">Lists</span></span>

> [!NOTE]
<span data-ttu-id="93c65-105">Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.</span><span class="sxs-lookup"><span data-stu-id="93c65-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="93c65-106">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="93c65-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="93c65-107">En F#, une liste est une série immuable et ordonnée d'éléments du même type.</span><span class="sxs-lookup"><span data-stu-id="93c65-107">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="93c65-108">Pour effectuer des opérations de base sur les listes, utilisez les fonctions dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="93c65-108">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>


## <a name="creating-and-initializing-lists"></a><span data-ttu-id="93c65-109">Création et initialisation de listes</span><span class="sxs-lookup"><span data-stu-id="93c65-109">Creating and Initializing Lists</span></span>
<span data-ttu-id="93c65-110">Vous pouvez définir une liste en répertoriant de manière explicite les éléments, séparés par des points-virgules et placés entre crochets, comme indiqué dans la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="93c65-110">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="93c65-111">Vous pouvez également insérer des sauts de ligne entre les éléments, les points-virgules étant facultatifs dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="93c65-111">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="93c65-112">Cette syntaxe produit du code plus lisible quand les expressions d'initialisation des éléments sont plus longues, ou quand vous souhaitez ajouter un commentaire pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="93c65-112">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="93c65-113">Généralement, tous les éléments de liste doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="93c65-113">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="93c65-114">Il existe une exception : une liste dont les éléments sont spécifiés comme type de base peut comporter des éléments qui sont des types dérivés.</span><span class="sxs-lookup"><span data-stu-id="93c65-114">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="93c65-115">L'exemple suivant est acceptable, car `Button` et `CheckBox` dérivent de `Control`.</span><span class="sxs-lookup"><span data-stu-id="93c65-115">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="93c65-116">Vous pouvez également définir des éléments de liste à l'aide d'une plage indiquée par des entiers séparés par l'opérateur de plage (`..`), comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="93c65-116">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="93c65-117">Une liste vide est spécifiée par une paire de crochets vide.</span><span class="sxs-lookup"><span data-stu-id="93c65-117">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="93c65-118">Vous pouvez également utiliser une expression de séquence pour créer une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-118">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="93c65-119">Consultez [Expressions de séquence](sequences.md#sequence-expressions) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="93c65-119">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="93c65-120">Par exemple, le code suivant crée une liste d'entiers au carré, de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="93c65-120">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="93c65-121">Opérateurs utilisés avec les listes</span><span class="sxs-lookup"><span data-stu-id="93c65-121">Operators for Working with Lists</span></span>
<span data-ttu-id="93c65-122">Vous pouvez joindre des éléments à une liste en utilisant l'opérateur (cons) `::`.</span><span class="sxs-lookup"><span data-stu-id="93c65-122">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="93c65-123">Si `list1` est `[2; 3; 4]`, le code suivant crée `list2` sous la forme `[100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="93c65-123">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="93c65-124">Vous pouvez concaténer des listes qui présentent des types compatibles à l'aide de l'opérateur `@`, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="93c65-124">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="93c65-125">Si `list1` est `[2; 3; 4]` et `list2` est `[100; 2; 3; 4 ]`, ce code crée `list3` sous la forme `[2; 3; 4; 100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="93c65-125">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4 ]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="93c65-126">Fonctions permettant d’effectuer des opérations sur les listes sont disponibles dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="93c65-126">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="93c65-127">En F#, les listes étant immuables, toute opération de changement a pour effet de générer de nouvelles listes au lieu de modifier les listes existantes.</span><span class="sxs-lookup"><span data-stu-id="93c65-127">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="93c65-128">Listes dans F # sont implémentées comme des listes liées uniques, ce qui signifie que les opérations qui accèdent seulement au début de la liste sont o (1), et l’accès aux éléments est O (*n*).</span><span class="sxs-lookup"><span data-stu-id="93c65-128">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>


## <a name="properties"></a><span data-ttu-id="93c65-129">Propriétés</span><span class="sxs-lookup"><span data-stu-id="93c65-129">Properties</span></span>
<span data-ttu-id="93c65-130">Le type de liste prend en charge les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="93c65-130">The list type supports the following properties:</span></span>

|<span data-ttu-id="93c65-131">Propriété</span><span class="sxs-lookup"><span data-stu-id="93c65-131">Property</span></span>|<span data-ttu-id="93c65-132">Type</span><span class="sxs-lookup"><span data-stu-id="93c65-132">Type</span></span>|<span data-ttu-id="93c65-133">Description</span><span class="sxs-lookup"><span data-stu-id="93c65-133">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="93c65-134">Head</span><span class="sxs-lookup"><span data-stu-id="93c65-134">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="93c65-135">Premier élément.</span><span class="sxs-lookup"><span data-stu-id="93c65-135">The first element.</span></span>|
|[<span data-ttu-id="93c65-136">Vide</span><span class="sxs-lookup"><span data-stu-id="93c65-136">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="93c65-137">Propriété statique qui retourne une liste vide du type approprié.</span><span class="sxs-lookup"><span data-stu-id="93c65-137">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="93c65-138">La fonction IsEmpty</span><span class="sxs-lookup"><span data-stu-id="93c65-138">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="93c65-139">`true` si la liste ne comporte aucun élément.</span><span class="sxs-lookup"><span data-stu-id="93c65-139">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="93c65-140">Item</span><span class="sxs-lookup"><span data-stu-id="93c65-140">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="93c65-141">Élément au niveau de l'index spécifié (de base zéro).</span><span class="sxs-lookup"><span data-stu-id="93c65-141">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="93c65-142">Longueur</span><span class="sxs-lookup"><span data-stu-id="93c65-142">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="93c65-143">Nombre d'éléments.</span><span class="sxs-lookup"><span data-stu-id="93c65-143">The number of elements.</span></span>|
|[<span data-ttu-id="93c65-144">Fin du</span><span class="sxs-lookup"><span data-stu-id="93c65-144">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="93c65-145">Liste sans premier élément.</span><span class="sxs-lookup"><span data-stu-id="93c65-145">The list without the first element.</span></span>|
<span data-ttu-id="93c65-146">Voici quelques exemples d'utilisation de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="93c65-146">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]
    
## <a name="using-lists"></a><span data-ttu-id="93c65-147">Utilisation de listes</span><span class="sxs-lookup"><span data-stu-id="93c65-147">Using Lists</span></span>
<span data-ttu-id="93c65-148">La programmation à l'aide de listes vous permet d'effectuer des opérations complexes avec peu de code.</span><span class="sxs-lookup"><span data-stu-id="93c65-148">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="93c65-149">Cette section décrit des opérations courantes sur des listes qui sont importantes pour la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="93c65-149">This section describes common operations on lists that are important to functional programming.</span></span>


### <a name="recursion-with-lists"></a><span data-ttu-id="93c65-150">Récursivité avec des listes</span><span class="sxs-lookup"><span data-stu-id="93c65-150">Recursion with Lists</span></span>
<span data-ttu-id="93c65-151">Les listes sont particulièrement adaptées aux techniques de programmation récursive.</span><span class="sxs-lookup"><span data-stu-id="93c65-151">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="93c65-152">Prenons en compte une opération à effectuer sur chaque élément d'une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-152">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="93c65-153">Vous pouvez procéder de manière récursive en effectuant l'opération sur le début de la liste, puis en passant à la fin de la liste, qui est une liste plus petite comprenant la liste d'origine sans le premier élément, et en revenant au niveau suivant de récursivité.</span><span class="sxs-lookup"><span data-stu-id="93c65-153">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="93c65-154">Pour écrire ce type de fonction récursive, utilisez l'opérateur cons (`::`) dans les critères spéciaux, qui vous permet de séparer le début d'une liste de sa fin.</span><span class="sxs-lookup"><span data-stu-id="93c65-154">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="93c65-155">L'exemple de code suivant indique comment utiliser les critères spéciaux pour implémenter une fonction récursive qui exécute des opérations sur une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-155">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="93c65-156">Le code précédent fonctionne bien dans le cas de petites listes, mais dans le cas de listes plus longues, il peut entraîner un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="93c65-156">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="93c65-157">Le code suivant améliore le précédent à l'aide d'un argument d'accumulation, technique standard utilisée avec les fonctions récursives.</span><span class="sxs-lookup"><span data-stu-id="93c65-157">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="93c65-158">L'argument d'accumulation rend la fin de la fonction récursive, ce qui permet de contenir l'espace de pile.</span><span class="sxs-lookup"><span data-stu-id="93c65-158">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="93c65-159">La fonction `RemoveAllMultiples` est récursive et accepte deux listes.</span><span class="sxs-lookup"><span data-stu-id="93c65-159">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="93c65-160">La première liste contient les nombres dont les multiples seront supprimés ; la seconde liste contient les nombres à supprimer.</span><span class="sxs-lookup"><span data-stu-id="93c65-160">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="93c65-161">Le code de l'exemple suivant utilise cette fonction récursive pour éliminer tous les nombres non premiers d'une liste, générant ainsi une liste de nombres premiers.</span><span class="sxs-lookup"><span data-stu-id="93c65-161">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="93c65-162">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-162">The output is as follows:</span></span>

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="93c65-163">Fonctions de module</span><span class="sxs-lookup"><span data-stu-id="93c65-163">Module Functions</span></span>
<span data-ttu-id="93c65-164">Le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) fournit des fonctions qui accèdent aux éléments d’une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-164">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="93c65-165">L'élément de début offre l'accès le plus simple et rapide.</span><span class="sxs-lookup"><span data-stu-id="93c65-165">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="93c65-166">Utilisez la propriété [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) ou la fonction module [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span><span class="sxs-lookup"><span data-stu-id="93c65-166">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="93c65-167">Vous pouvez accéder à la fin d’une liste à l’aide de la [fin](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) propriété ou le [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) (fonction).</span><span class="sxs-lookup"><span data-stu-id="93c65-167">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="93c65-168">Pour rechercher un élément par index, utilisez la [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) (fonction).</span><span class="sxs-lookup"><span data-stu-id="93c65-168">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="93c65-169">`List.nth` parcourt la liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-169">`List.nth` traverses the list.</span></span> <span data-ttu-id="93c65-170">Par conséquent, il est O (*n*).</span><span class="sxs-lookup"><span data-stu-id="93c65-170">Therefore, it is O(*n*).</span></span> <span data-ttu-id="93c65-171">Si votre code utilise fréquemment `List.nth`, envisagez d'utiliser un tableau à la place d'une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-171">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="93c65-172">L'accès aux éléments des tableaux est O(1).</span><span class="sxs-lookup"><span data-stu-id="93c65-172">Element access in arrays is O(1).</span></span>


### <a name="boolean-operations-on-lists"></a><span data-ttu-id="93c65-173">Opérations booléennes sur des listes</span><span class="sxs-lookup"><span data-stu-id="93c65-173">Boolean Operations on Lists</span></span>
<span data-ttu-id="93c65-174">Le [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) fonction détermine si une liste comporte tous les éléments.</span><span class="sxs-lookup"><span data-stu-id="93c65-174">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="93c65-175">Le [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) fonction s’applique à une valeur booléenne test à des éléments d’une liste et retourne `true` si un élément satisfait au test.</span><span class="sxs-lookup"><span data-stu-id="93c65-175">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="93c65-176">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) est semblable, mais fonctionne sur des paires d’éléments dans deux listes successives.</span><span class="sxs-lookup"><span data-stu-id="93c65-176">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="93c65-177">Le code suivant montre l'utilisation de `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="93c65-177">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="93c65-178">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-178">The output is as follows:</span></span>

```
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="93c65-179">L'exemple suivant montre l'utilisation de `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="93c65-179">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="93c65-180">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-180">The output is as follows:</span></span>

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="93c65-181">Vous pouvez utiliser [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) si vous souhaitez tester si tous les éléments d’une liste satisfont à une condition.</span><span class="sxs-lookup"><span data-stu-id="93c65-181">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="93c65-182">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-182">The output is as follows:</span></span>

```
true
false
```

<span data-ttu-id="93c65-183">De même, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) détermine si tous les éléments des positions correspondantes dans les deux listes satisfont à une expression booléenne qui implique chaque paire d’éléments.</span><span class="sxs-lookup"><span data-stu-id="93c65-183">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="93c65-184">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-184">The output is as follows:</span></span>

```
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="93c65-185">Opérations de tri sur des listes</span><span class="sxs-lookup"><span data-stu-id="93c65-185">Sort Operations on Lists</span></span>
<span data-ttu-id="93c65-186">Le [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), et [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) fonctions trient les listes.</span><span class="sxs-lookup"><span data-stu-id="93c65-186">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="93c65-187">La fonction de tri détermine laquelle de ces trois fonctions utiliser.</span><span class="sxs-lookup"><span data-stu-id="93c65-187">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="93c65-188">`List.sort` utilise la comparaison générique par défaut.</span><span class="sxs-lookup"><span data-stu-id="93c65-188">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="93c65-189">Celle-ci compare des valeurs à l'aide d'opérateurs globaux reposant sur la fonction de comparaison générique.</span><span class="sxs-lookup"><span data-stu-id="93c65-189">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="93c65-190">Elle est efficace avec une large gamme de types d'éléments, tels que les types numériques simples, les tuples, les enregistrements, les unions discriminées, les listes, les tableaux et tout type qui implémente `System.IComparable`.</span><span class="sxs-lookup"><span data-stu-id="93c65-190">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="93c65-191">Dans le cas des types implémentant `System.IComparable`, la comparaison générique utilise la fonction `System.IComparable.CompareTo()`.</span><span class="sxs-lookup"><span data-stu-id="93c65-191">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="93c65-192">La comparaison générique fonctionne aussi avec les chaînes, mais utilise un ordre de tri indépendant de la culture.</span><span class="sxs-lookup"><span data-stu-id="93c65-192">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="93c65-193">Elle ne doit pas être utilisée sur les types non pris en charge, tels que les types de fonction.</span><span class="sxs-lookup"><span data-stu-id="93c65-193">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="93c65-194">De plus, les performances de la comparaison générique par défaut sont meilleures dans le cas de petits types structurés. Dans le cas de types structurés plus importants qui impliquent une fréquence de comparaison et de tri plus soutenue, envisagez d'implémenter `System.IComparable` et de fournir une implémentation efficace de la méthode `System.IComparable.CompareTo()`.</span><span class="sxs-lookup"><span data-stu-id="93c65-194">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="93c65-195">`List.sortBy` accepte une fonction qui retourne une valeur utilisée comme critère de tri, et `List.sortWith` accepte une fonction de comparaison comme argument.</span><span class="sxs-lookup"><span data-stu-id="93c65-195">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="93c65-196">Ces deux fonctions sont utiles quand les types ne prennent pas en charge la comparaison ou quand la comparaison nécessite une sémantique plus complexe, comme avec les chaînes prenant en compte la culture.</span><span class="sxs-lookup"><span data-stu-id="93c65-196">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="93c65-197">L'exemple suivant montre l'utilisation de `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="93c65-197">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="93c65-198">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-198">The output is as follows:</span></span>

```
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="93c65-199">L'exemple suivant montre l'utilisation de `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="93c65-199">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="93c65-200">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-200">The output is as follows:</span></span>

```
[1; -2; 4; 5; 8]
```

<span data-ttu-id="93c65-201">L'exemple suivant montre l'utilisation de `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="93c65-201">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="93c65-202">Dans cet exemple, la fonction de comparaison personnalisée `compareWidgets` est utilisée pour comparer en premier un champ de type personnalisé, puis un autre champ quand les valeurs du premier champ sont égales.</span><span class="sxs-lookup"><span data-stu-id="93c65-202">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="93c65-203">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-203">The output is as follows:</span></span>

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="93c65-204">Opérations de recherche sur des listes</span><span class="sxs-lookup"><span data-stu-id="93c65-204">Search Operations on Lists</span></span>
<span data-ttu-id="93c65-205">Les listes prennent en charge plusieurs opérations de recherche.</span><span class="sxs-lookup"><span data-stu-id="93c65-205">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="93c65-206">La plus simple, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), vous permet de rechercher le premier élément qui correspond à une condition donnée.</span><span class="sxs-lookup"><span data-stu-id="93c65-206">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="93c65-207">L'exemple de code suivant montre l'utilisation de `List.find` pour rechercher le premier nombre divisible par 5 dans une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-207">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="93c65-208">Le résultat est 5.</span><span class="sxs-lookup"><span data-stu-id="93c65-208">The result is 5.</span></span>

<span data-ttu-id="93c65-209">Si les éléments doivent être transformés au préalable, appelez [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), qui prend une fonction retournant une option, et que la valeur de recherche pour la première option qui est `Some(x)`.</span><span class="sxs-lookup"><span data-stu-id="93c65-209">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="93c65-210">Au lieu de renvoyer l'élément, `List.pick` retourne le résultat `x`.</span><span class="sxs-lookup"><span data-stu-id="93c65-210">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="93c65-211">Si aucun élément correspondant n'est trouvé, `List.pick` lève `System.Collections.Generic.KeyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="93c65-211">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="93c65-212">Le code suivant illustre l'utilisation de `List.pick`.</span><span class="sxs-lookup"><span data-stu-id="93c65-212">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="93c65-213">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-213">The output is as follows:</span></span>

```
"b"
```

<span data-ttu-id="93c65-214">Un autre groupe d’opérations de recherche, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) et fonctions connexes, génèrent une valeur d’option.</span><span class="sxs-lookup"><span data-stu-id="93c65-214">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="93c65-215">La fonction `List.tryFind` retourne le premier élément d'une liste qui satisfait à une condition, le cas échéant, et la valeur d'option `None` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="93c65-215">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="93c65-216">La variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) retourne l’index de l’élément, s’il en trouve, au lieu de l’élément lui-même.</span><span class="sxs-lookup"><span data-stu-id="93c65-216">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="93c65-217">Ces fonctions sont illustrées dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="93c65-217">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="93c65-218">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-218">The output is as follows:</span></span>

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="93c65-219">Opérations arithmétiques sur des listes</span><span class="sxs-lookup"><span data-stu-id="93c65-219">Arithmetic Operations on Lists</span></span>
<span data-ttu-id="93c65-220">Les opérations arithmétiques courantes telles que la somme et moyenne sont générées dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="93c65-220">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="93c65-221">Pour travailler avec [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), le type d’élément de liste doit prendre en charge la `+` opérateur et ont une valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="93c65-221">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="93c65-222">Tous les types arithmétiques intégrés remplissent ces conditions.</span><span class="sxs-lookup"><span data-stu-id="93c65-222">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="93c65-223">Pour travailler avec [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), le type d’élément doit prendre en charge la division sans reste, ce qui exclut les types intégraux, mais autorise les types à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="93c65-223">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="93c65-224">Le [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) et [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) fonctions acceptent une fonction en tant que paramètre, et les résultats de cette fonction sont utilisés pour calculer les valeurs de la somme ou la moyenne.</span><span class="sxs-lookup"><span data-stu-id="93c65-224">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="93c65-225">Le code suivant montre l'utilisation de `List.sum`, `List.sumBy` et `List.average`.</span><span class="sxs-lookup"><span data-stu-id="93c65-225">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="93c65-226">Le résultat est `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="93c65-226">The output is `1.000000`.</span></span>

<span data-ttu-id="93c65-227">Le code suivant illustre l'utilisation de `List.averageBy`.</span><span class="sxs-lookup"><span data-stu-id="93c65-227">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="93c65-228">Le résultat est `5.5`.</span><span class="sxs-lookup"><span data-stu-id="93c65-228">The output is `5.5`.</span></span>


### <a name="lists-and-tuples"></a><span data-ttu-id="93c65-229">Listes et tuples</span><span class="sxs-lookup"><span data-stu-id="93c65-229">Lists and Tuples</span></span>
<span data-ttu-id="93c65-230">Les listes qui contiennent des tuples peuvent être manipulées par des fonctions de compression et de décompression.</span><span class="sxs-lookup"><span data-stu-id="93c65-230">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="93c65-231">Ces fonctions combinent deux listes de valeurs uniques en une seule liste de tuples ou séparent une liste de tuples en deux listes de valeurs uniques.</span><span class="sxs-lookup"><span data-stu-id="93c65-231">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="93c65-232">Le plus simple [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) fonction prend deux listes d’éléments uniques et produit une seule liste de paires de tuples.</span><span class="sxs-lookup"><span data-stu-id="93c65-232">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="93c65-233">Une autre version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), prend trois listes d’éléments uniques et produit une seule liste de tuples comportant trois éléments.</span><span class="sxs-lookup"><span data-stu-id="93c65-233">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="93c65-234">L'exemple de code suivant montre l'utilisation de `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="93c65-234">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="93c65-235">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-235">The output is as follows:</span></span>

```
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="93c65-236">L'exemple de code suivant montre l'utilisation de `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="93c65-236">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="93c65-237">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-237">The output is as follows:</span></span>

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="93c65-238">Correspondants versions de décompression, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) et [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), prennent des listes de tuples et retournent les listes dans un tuple, où la première liste contienne tous les éléments qui étaient initialement dans chaque tuple et seconde liste contient le deuxième élément de chaque tuple et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="93c65-238">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="93c65-239">L’exemple de code suivant illustre l’utilisation de [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="93c65-239">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="93c65-240">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-240">The output is as follows:</span></span>

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="93c65-241">L’exemple de code suivant illustre l’utilisation de [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="93c65-241">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="93c65-242">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-242">The output is as follows:</span></span>

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="93c65-243">Opérations sur les éléments de liste</span><span class="sxs-lookup"><span data-stu-id="93c65-243">Operating on List Elements</span></span>
<span data-ttu-id="93c65-244">F# prend en charge un éventail d'opérations sur des éléments de liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-244">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="93c65-245">La plus simple est [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), ce qui vous permet d’appeler une fonction sur chaque élément d’une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-245">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="93c65-246">Incluent des variations [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), ce qui vous permet d’effectuer une opération sur les éléments de deux listes, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), ce qui revient à `List.iter` , sauf que l’index de chaque élément est passé en tant qu’un l’argument de la fonction qui est appelée pour chaque élément, et [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), qui est une combinaison des fonctionnalités de `List.iter2` et `List.iteri`.</span><span class="sxs-lookup"><span data-stu-id="93c65-246">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="93c65-247">L'exemple de code suivant illustre ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="93c65-247">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="93c65-248">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-248">The output is as follows:</span></span>

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

<span data-ttu-id="93c65-249">Une autre fonction fréquemment utilisée qui transforme des éléments de liste est [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), qui permet d’appliquer une fonction à chaque élément d’une liste et de placer tous les résultats dans une nouvelle liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-249">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="93c65-250">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) et [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) sont des variations qui prennent plusieurs listes.</span><span class="sxs-lookup"><span data-stu-id="93c65-250">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="93c65-251">Vous pouvez également utiliser [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) et [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), si, en plus de l’élément, la fonction doit être passée à l’index de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="93c65-251">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="93c65-252">La seule différence entre `List.mapi2` et `List.mapi` est le fait que `List.mapi2` fonctionne avec les deux listes.</span><span class="sxs-lookup"><span data-stu-id="93c65-252">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="93c65-253">L’exemple suivant illustre [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span><span class="sxs-lookup"><span data-stu-id="93c65-253">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="93c65-254">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-254">The output is as follows:</span></span>

```
[2; 3; 4]
```

<span data-ttu-id="93c65-255">L'exemple suivant montre l'utilisation de `List.map2`.</span><span class="sxs-lookup"><span data-stu-id="93c65-255">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="93c65-256">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-256">The output is as follows:</span></span>

```
[5; 7; 9]
```

<span data-ttu-id="93c65-257">L'exemple suivant montre l'utilisation de `List.map3`.</span><span class="sxs-lookup"><span data-stu-id="93c65-257">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="93c65-258">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-258">The output is as follows:</span></span>

```
[7; 10; 13]
```

<span data-ttu-id="93c65-259">L'exemple suivant montre l'utilisation de `List.mapi`.</span><span class="sxs-lookup"><span data-stu-id="93c65-259">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="93c65-260">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-260">The output is as follows:</span></span>

```
[1; 3; 5]
```

<span data-ttu-id="93c65-261">L'exemple suivant montre l'utilisation de `List.mapi2`.</span><span class="sxs-lookup"><span data-stu-id="93c65-261">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="93c65-262">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-262">The output is as follows:</span></span>

```
[0; 7; 18]
```

<span data-ttu-id="93c65-263">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) est similaire à `List.map`, sauf que chaque élément produit une liste et que toutes ces listes sont concaténées dans une liste finale.</span><span class="sxs-lookup"><span data-stu-id="93c65-263">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="93c65-264">Dans le code suivant, chaque élément de la liste génère trois nombres.</span><span class="sxs-lookup"><span data-stu-id="93c65-264">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="93c65-265">Ils sont tous rassemblés dans une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-265">These are all collected into one list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="93c65-266">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-266">The output is as follows:</span></span>

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="93c65-267">Vous pouvez également utiliser [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), qui prend une condition booléenne et produit une nouvelle liste composée uniquement des éléments qui satisfont la condition donnée.</span><span class="sxs-lookup"><span data-stu-id="93c65-267">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="93c65-268">La liste obtenue est `[2; 4; 6]`.</span><span class="sxs-lookup"><span data-stu-id="93c65-268">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="93c65-269">Une combinaison de mappage et de filtre, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) vous permet de transformer et de sélectionner des éléments en même temps.</span><span class="sxs-lookup"><span data-stu-id="93c65-269">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="93c65-270">`List.choose` applique une fonction qui retourne une option à chaque élément d'une liste et renvoie une nouvelle liste des résultats pour les éléments quand la fonction retourne la valeur d'option `Some`.</span><span class="sxs-lookup"><span data-stu-id="93c65-270">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="93c65-271">Le code suivant illustre l'utilisation de `List.choose` pour sélectionner des mots en majuscules dans une liste de mots.</span><span class="sxs-lookup"><span data-stu-id="93c65-271">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="93c65-272">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="93c65-272">The output is as follows:</span></span>

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="93c65-273">Opérations sur plusieurs listes</span><span class="sxs-lookup"><span data-stu-id="93c65-273">Operating on Multiple Lists</span></span>
<span data-ttu-id="93c65-274">Les listes peuvent être jointes.</span><span class="sxs-lookup"><span data-stu-id="93c65-274">Lists can be joined together.</span></span> <span data-ttu-id="93c65-275">Pour joindre deux listes, utilisez [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span><span class="sxs-lookup"><span data-stu-id="93c65-275">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="93c65-276">Pour joindre plus de deux listes, utilisez [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span><span class="sxs-lookup"><span data-stu-id="93c65-276">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]
    
### <a name="fold-and-scan-operations"></a><span data-ttu-id="93c65-277">Opérations de pliage et d’analyse</span><span class="sxs-lookup"><span data-stu-id="93c65-277">Fold and Scan Operations</span></span>
<span data-ttu-id="93c65-278">Certaines opérations de liste impliquent l'interdépendance entre tous les éléments de la liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-278">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="93c65-279">Les opérations de repli et d’analyse sont comme `List.iter` et `List.map` dans la mesure où vous appelez une fonction sur chaque élément, mais ces opérations fournissent un paramètre supplémentaire, appelé le *accumulation* qui achemine des informations le calcul.</span><span class="sxs-lookup"><span data-stu-id="93c65-279">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="93c65-280">Utilisez `List.fold` pour effectuer un calcul sur une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-280">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="93c65-281">L’exemple de code suivant illustre l’utilisation de [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) pour effectuer diverses opérations.</span><span class="sxs-lookup"><span data-stu-id="93c65-281">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="93c65-282">La liste est parcourue ; l'accumulateur `acc` est une valeur passée au cours du calcul.</span><span class="sxs-lookup"><span data-stu-id="93c65-282">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="93c65-283">Le premier argument prend l'accumulateur et l'élément de liste, puis retourne le résultat intermédiaire du calcul pour cet élément de liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-283">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="93c65-284">Le deuxième argument est la valeur initiale de l'accumulateur.</span><span class="sxs-lookup"><span data-stu-id="93c65-284">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="93c65-285">Les versions de ces fonctions dont le nom contient un chiffre s'effectuent sur plusieurs listes.</span><span class="sxs-lookup"><span data-stu-id="93c65-285">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="93c65-286">Par exemple, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) effectue des calculs sur deux listes.</span><span class="sxs-lookup"><span data-stu-id="93c65-286">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="93c65-287">L'exemple suivant montre l'utilisation de `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="93c65-287">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="93c65-288">`List.fold`et [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) diffèrent en ce que `List.fold` retourne la valeur finale du paramètre supplémentaire, mais `List.scan` retourne la liste des valeurs intermédiaires (avec la valeur finale) du paramètre supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="93c65-288">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="93c65-289">Chacune de ces fonctions inclut une variation inverse, par exemple, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), qui diffère de l’ordre dans lequel la liste est parcourue et l’ordre des arguments.</span><span class="sxs-lookup"><span data-stu-id="93c65-289">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="93c65-290">En outre, `List.fold` et `List.foldBack` présentent des variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) et [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), qui acceptent deux listes de longueur égale.</span><span class="sxs-lookup"><span data-stu-id="93c65-290">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="93c65-291">La fonction qui s'exécute sur chaque élément peut utiliser des éléments correspondants aux deux listes pour effectuer une action.</span><span class="sxs-lookup"><span data-stu-id="93c65-291">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="93c65-292">Les types d'éléments des deux listes peuvent être différents, comme dans l'exemple suivant, où une liste contient des montants de transactions sur un compte bancaire et l'autre contient le type de transaction : dépôt ou retrait.</span><span class="sxs-lookup"><span data-stu-id="93c65-292">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="93c65-293">Pour un calcul tel qu'une addition, `List.fold` et `List.foldBack` ont le même effet car le résultat ne dépend pas de l'ordre de traversée.</span><span class="sxs-lookup"><span data-stu-id="93c65-293">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="93c65-294">Dans l'exemple ci-dessous, `List.foldBack` est utilisé pour ajouter les éléments à une liste.</span><span class="sxs-lookup"><span data-stu-id="93c65-294">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="93c65-295">Voici à nouveau l'exemple du compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="93c65-295">The following example returns to the bank account example.</span></span> <span data-ttu-id="93c65-296">Cette fois, un nouveau type de transaction est ajouté : le calcul d'intérêts.</span><span class="sxs-lookup"><span data-stu-id="93c65-296">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="93c65-297">Le solde de fin dépend désormais de l’ordre des transactions.</span><span class="sxs-lookup"><span data-stu-id="93c65-297">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="93c65-298">La fonction [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) s’apparente à `List.fold` et `List.scan`, mais au lieu de passer un accumulateur séparé, `List.reduce` prend une fonction qui accepte deux arguments du type d’élément à la place de seul et que l’autre de ces arguments joue le rôle d’accumulateur, ce qui signifie qu’il stocke le résultat intermédiaire du calcul.</span><span class="sxs-lookup"><span data-stu-id="93c65-298">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="93c65-299">`List.reduce` commence par fonctionner sur les deux premiers éléments de liste, puis utilise le résultat de l'opération avec l'élément suivant.</span><span class="sxs-lookup"><span data-stu-id="93c65-299">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="93c65-300">Comme aucun accumulateur distinct ne possède son propre type, `List.reduce` ne peut être utilisé à la place de `List.fold` si l'accumulateur et le type d'élément ont le même type.</span><span class="sxs-lookup"><span data-stu-id="93c65-300">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="93c65-301">Le code suivant montre l'utilisation de `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="93c65-301">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="93c65-302">`List.reduce` lève une exception si la liste fournie ne comporte aucun élément.</span><span class="sxs-lookup"><span data-stu-id="93c65-302">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="93c65-303">Dans le code suivant, le premier appel à l'expression lambda reçoit les arguments 2 et 4, et retourne 6. L'appel suivant reçoit les arguments 6 et 10, le résultat est donc 16.</span><span class="sxs-lookup"><span data-stu-id="93c65-303">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]
    
### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="93c65-304">Conversion entre listes et autres types de collections</span><span class="sxs-lookup"><span data-stu-id="93c65-304">Converting Between Lists and Other Collection Types</span></span>
<span data-ttu-id="93c65-305">Le module `List` fournit des fonctions pour convertir vers et depuis des séquences et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="93c65-305">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="93c65-306">Pour convertir vers ou à partir d’une séquence, utilisez [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) ou [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span><span class="sxs-lookup"><span data-stu-id="93c65-306">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="93c65-307">Pour convertir vers ou à partir d’un tableau, utilisez [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) ou [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span><span class="sxs-lookup"><span data-stu-id="93c65-307">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>


### <a name="additional-operations"></a><span data-ttu-id="93c65-308">Opérations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="93c65-308">Additional Operations</span></span>
<span data-ttu-id="93c65-309">Pour plus d’informations sur d’autres opérations sur les listes, consultez la rubrique de référence de bibliothèque [Collections.List, Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="93c65-309">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>


## <a name="see-also"></a><span data-ttu-id="93c65-310">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93c65-310">See Also</span></span>
[<span data-ttu-id="93c65-311">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="93c65-311">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="93c65-312">Types F#</span><span class="sxs-lookup"><span data-stu-id="93c65-312">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="93c65-313">Séquences</span><span class="sxs-lookup"><span data-stu-id="93c65-313">Sequences</span></span>](sequences.md)

[<span data-ttu-id="93c65-314">Tableaux</span><span class="sxs-lookup"><span data-stu-id="93c65-314">Arrays</span></span>](arrays.md)

[<span data-ttu-id="93c65-315">Options</span><span class="sxs-lookup"><span data-stu-id="93c65-315">Options</span></span>](options.md)
