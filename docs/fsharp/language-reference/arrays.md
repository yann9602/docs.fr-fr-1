---
title: Tableaux (F#)
description: "Découvrez comment créer et utiliser des tableaux dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 61fa9084-abdc-4cf5-8213-91ec1211866b
ms.openlocfilehash: 7c9d8405230f4d765d3afdeaa154ddc598d0d1ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="arrays"></a><span data-ttu-id="f0040-104">Tableaux</span><span class="sxs-lookup"><span data-stu-id="f0040-104">Arrays</span></span>

> [!NOTE]
<span data-ttu-id="f0040-105">Le lien des informations de référence sur les API pointe vers MSDN.</span><span class="sxs-lookup"><span data-stu-id="f0040-105">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="f0040-106">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="f0040-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="f0040-107">Les tableaux sont des collections de taille fixe, de base zéro et mutables d’éléments de données consécutifs qui sont tous du même type.</span><span class="sxs-lookup"><span data-stu-id="f0040-107">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="f0040-108">Création de tableaux</span><span class="sxs-lookup"><span data-stu-id="f0040-108">Creating Arrays</span></span>
<span data-ttu-id="f0040-109">Vous pouvez créer des tableaux de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="f0040-109">You can create arrays in several ways.</span></span> <span data-ttu-id="f0040-110">Vous pouvez créer un petit tableau en répertoriant des valeurs consécutives entre `[|` et `|]` et séparées par des points-virgules, comme illustré dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="f0040-110">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="f0040-111">Vous pouvez également placer chaque élément sur une ligne distincte, auquel cas le point-virgule de séparation est facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0040-111">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="f0040-112">Le type des éléments du tableau est déduit des littéraux utilisés et doit être cohérent.</span><span class="sxs-lookup"><span data-stu-id="f0040-112">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="f0040-113">Le code suivant génère une erreur, car 1.0 est une valeur float et 2 et 3 sont des entiers.</span><span class="sxs-lookup"><span data-stu-id="f0040-113">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="f0040-114">Vous pouvez également utiliser des expressions de séquence pour créer des tableaux.</span><span class="sxs-lookup"><span data-stu-id="f0040-114">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="f0040-115">Voici un exemple qui crée un tableau des carrés des entiers de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="f0040-115">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="f0040-116">Pour créer un tableau dans lequel tous les éléments sont initialisés à zéro, utilisez `Array.zeroCreate`.</span><span class="sxs-lookup"><span data-stu-id="f0040-116">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]
    
## <a name="accessing-elements"></a><span data-ttu-id="f0040-117">L’accès aux éléments</span><span class="sxs-lookup"><span data-stu-id="f0040-117">Accessing Elements</span></span>

<span data-ttu-id="f0040-118">Vous pouvez accéder à des éléments de tableau à l’aide d’un opérateur point (`.`) et des crochets (`[` et `]`).</span><span class="sxs-lookup"><span data-stu-id="f0040-118">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="f0040-119">Index de tableau commencent à 0.</span><span class="sxs-lookup"><span data-stu-id="f0040-119">Array indexes start at 0.</span></span>

<span data-ttu-id="f0040-120">Vous pouvez également accéder à des éléments de tableau à l’aide de notation de découpage, ce qui vous permet de spécifier une sous-plage du tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-120">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="f0040-121">Voici quelques exemples de notation de découpage.</span><span class="sxs-lookup"><span data-stu-id="f0040-121">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="f0040-122">Lors de la notation de découpage est utilisée, une nouvelle copie du tableau est créée.</span><span class="sxs-lookup"><span data-stu-id="f0040-122">When slice notation is used, a new copy of the array is created.</span></span>


## <a name="array-types-and-modules"></a><span data-ttu-id="f0040-123">Modules et Types de tableau</span><span class="sxs-lookup"><span data-stu-id="f0040-123">Array Types and Modules</span></span>
<span data-ttu-id="f0040-124">Le type de tous les tableaux F # est le type .NET Framework <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0040-124">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f0040-125">Par conséquent, les tableaux F # prennent en charge toutes les fonctionnalités disponibles dans <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0040-125">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f0040-126">Le module de bibliothèque [ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) prend en charge les opérations sur les tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="f0040-126">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="f0040-127">Les modules `Array2D`, `Array3D`, et `Array4D` contiennent des fonctions qui prennent en charge les opérations sur les tableaux de deux, trois et quatre dimensions, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f0040-127">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="f0040-128">Vous pouvez créer des tableaux de rang supérieur à quatre à l’aide de <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0040-128">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="f0040-129">Fonctions simples</span><span class="sxs-lookup"><span data-stu-id="f0040-129">Simple Functions</span></span>
<span data-ttu-id="f0040-130">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)Obtient un élément.</span><span class="sxs-lookup"><span data-stu-id="f0040-130">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="f0040-131">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)donne la longueur d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-131">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="f0040-132">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)définit un élément à une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f0040-132">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="f0040-133">L’exemple de code suivant illustre l’utilisation de ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="f0040-133">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="f0040-134">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="f0040-134">The output is as follows.</span></span>

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="f0040-135">Fonctions qui créent des tableaux</span><span class="sxs-lookup"><span data-stu-id="f0040-135">Functions That Create Arrays</span></span>

<span data-ttu-id="f0040-136">Plusieurs fonctions de créer des tableaux sans nécessiter un tableau existant.</span><span class="sxs-lookup"><span data-stu-id="f0040-136">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="f0040-137">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)Crée un tableau qui ne contient-elle pas d’éléments.</span><span class="sxs-lookup"><span data-stu-id="f0040-137">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="f0040-138">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)Crée un tableau d’une taille spécifiée et affecte tous les éléments de valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="f0040-138">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="f0040-139">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)Crée un tableau, en fonction d’une dimension et une fonction pour générer les éléments.</span><span class="sxs-lookup"><span data-stu-id="f0040-139">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="f0040-140">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)Crée un tableau dans lequel tous les éléments sont initialisés à la valeur zéro pour le type du tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-140">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="f0040-141">Le code suivant illustre ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="f0040-141">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="f0040-142">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="f0040-142">The output is as follows.</span></span>

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="f0040-143">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)Crée un tableau qui contient des éléments copiés à partir d’un tableau existant.</span><span class="sxs-lookup"><span data-stu-id="f0040-143">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="f0040-144">Notez que la copie est une copie superficielle, ce qui signifie que si le type d’élément est un type référence, uniquement la référence est copiée, pas l’objet sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="f0040-144">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="f0040-145">L'exemple de code suivant illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="f0040-145">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="f0040-146">La sortie du code précédent est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f0040-146">The output of the preceding code is as follows:</span></span>

```
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="f0040-147">La chaîne `Test1` s’affiche uniquement dans le premier tableau parce que l’opération de création d’un nouvel élément remplace la référence dans `firstArray` mais n’affecte ne pas la référence d’origine à une chaîne vide est toujours présente dans `secondArray`.</span><span class="sxs-lookup"><span data-stu-id="f0040-147">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="f0040-148">La chaîne `Test2` s’affiche dans les deux tableaux, car le `Insert` opération sur le <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affecte sous-jacent <xref:System.Text.StringBuilder?displayProperty=nameWithType> objet, qui est référencé dans les deux tableaux.</span><span class="sxs-lookup"><span data-stu-id="f0040-148">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="f0040-149">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)génère un nouveau tableau à partir d’une sous-plage d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-149">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="f0040-150">Vous spécifiez la sous-plage en fournissant l’index de départ et la longueur.</span><span class="sxs-lookup"><span data-stu-id="f0040-150">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="f0040-151">Le code suivant montre l'utilisation de `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="f0040-151">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="f0040-152">La sortie indique que le sous-tableau démarre à l’élément 5 et contienne 10 éléments.</span><span class="sxs-lookup"><span data-stu-id="f0040-152">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
<span data-ttu-id="f0040-153">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)Crée un nouveau tableau combinant deux tableaux existants.</span><span class="sxs-lookup"><span data-stu-id="f0040-153">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="f0040-154">Le code suivant montre comment **Array.append**.</span><span class="sxs-lookup"><span data-stu-id="f0040-154">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="f0040-155">La sortie du code précédent est comme suit.</span><span class="sxs-lookup"><span data-stu-id="f0040-155">The output of the preceding code is as follows.</span></span>

```
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="f0040-156">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)Sélectionne les éléments d’un tableau à inclure dans un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-156">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="f0040-157">Le code suivant montre comment `Array.choose`.</span><span class="sxs-lookup"><span data-stu-id="f0040-157">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="f0040-158">Notez que le type d’élément du tableau n’est pas nécessairement correspond au type de la valeur retournée dans le type d’option.</span><span class="sxs-lookup"><span data-stu-id="f0040-158">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="f0040-159">Dans cet exemple, le type d’élément est `int` et l’option est le résultat d’une fonction polynomiale, `elem*elem - 1`, comme flottante point nombre.</span><span class="sxs-lookup"><span data-stu-id="f0040-159">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="f0040-160">La sortie du code précédent est comme suit.</span><span class="sxs-lookup"><span data-stu-id="f0040-160">The output of the preceding code is as follows.</span></span>

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="f0040-161">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)exécute une fonction spécifiée sur chaque élément du tableau d’un tableau existant puis collecte les éléments générés par la fonction et les combine dans un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-161">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="f0040-162">Le code suivant montre comment `Array.collect`.</span><span class="sxs-lookup"><span data-stu-id="f0040-162">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="f0040-163">La sortie du code précédent est comme suit.</span><span class="sxs-lookup"><span data-stu-id="f0040-163">The output of the preceding code is as follows.</span></span>

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="f0040-164">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)prend une séquence de tableaux et les combine dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-164">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="f0040-165">Le code suivant montre comment `Array.concat`.</span><span class="sxs-lookup"><span data-stu-id="f0040-165">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="f0040-166">La sortie du code précédent est comme suit.</span><span class="sxs-lookup"><span data-stu-id="f0040-166">The output of the preceding code is as follows.</span></span>

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="f0040-167">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)prend une fonction de condition booléenne et génère un nouveau tableau qui contient uniquement les éléments du tableau d’entrée pour lesquels la condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="f0040-167">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="f0040-168">Le code suivant montre comment `Array.filter`.</span><span class="sxs-lookup"><span data-stu-id="f0040-168">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="f0040-169">La sortie du code précédent est comme suit.</span><span class="sxs-lookup"><span data-stu-id="f0040-169">The output of the preceding code is as follows.</span></span>

```
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="f0040-170">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)génère un nouveau tableau en inversant l’ordre d’un tableau existant.</span><span class="sxs-lookup"><span data-stu-id="f0040-170">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="f0040-171">Le code suivant montre comment `Array.rev`.</span><span class="sxs-lookup"><span data-stu-id="f0040-171">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

<span data-ttu-id="f0040-172">La sortie du code précédent est comme suit.</span><span class="sxs-lookup"><span data-stu-id="f0040-172">The output of the preceding code is as follows.</span></span>

```
"Hello world!"
```

<span data-ttu-id="f0040-173">Vous pouvez facilement combiner des fonctions du module array qui transforment les tableaux à l’aide de l’opérateur de pipeline (`|>`), comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f0040-173">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="f0040-174">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f0040-174">The output is</span></span>

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="f0040-175">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="f0040-175">Multidimensional Arrays</span></span>

<span data-ttu-id="f0040-176">Un tableau multidimensionnel peut être créé, mais il n’existe aucune syntaxe pour l’écriture d’un littéral de tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="f0040-176">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="f0040-177">Utilisez l’opérateur [ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) pour créer un tableau à partir d’une séquence de séquences d’éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-177">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="f0040-178">Les séquences peuvent être des littéraux de tableau ou de liste.</span><span class="sxs-lookup"><span data-stu-id="f0040-178">The sequences can be array or list literals.</span></span> <span data-ttu-id="f0040-179">Par exemple, le code suivant crée un tableau à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="f0040-179">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="f0040-180">Vous pouvez également utiliser la fonction [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) pour initialiser des tableaux de deux dimensions et même des fonctions sont disponibles pour les tableaux de trois et quatre dimensions.</span><span class="sxs-lookup"><span data-stu-id="f0040-180">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="f0040-181">Ces fonctions acceptent une fonction qui est utilisée pour créer les éléments.</span><span class="sxs-lookup"><span data-stu-id="f0040-181">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="f0040-182">Pour créer un tableau à deux dimensions qui contient les éléments pour définir une valeur initiale au lieu de spécifier une fonction, utilisez la [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) (fonction), qui est également disponible pour les tableaux jusqu'à quatre dimensions.</span><span class="sxs-lookup"><span data-stu-id="f0040-182">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="f0040-183">L’exemple de code suivant tout d’abord comment créer un tableau de tableaux qui contiennent les éléments souhaités, puis utilise `Array2D.init` pour générer le tableau à deux dimensions souhaité.</span><span class="sxs-lookup"><span data-stu-id="f0040-183">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="f0040-184">Tableau d’indexation et de découpage de syntaxe est prise en charge pour les tableaux jusqu'à rang 4.</span><span class="sxs-lookup"><span data-stu-id="f0040-184">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="f0040-185">Lorsque vous spécifiez un index dans plusieurs dimensions, vous utilisez des virgules pour séparer les index, comme illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f0040-185">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]
    
<span data-ttu-id="f0040-186">Le type d’un tableau à deux dimensions est écrit en tant que `<type>[,]` (par exemple, `int[,]`, `double[,]`), et le type d’un tableau tridimensionnel est écrit en tant que `<type>[,,]`, et ainsi de suite pour les tableaux de dimensions supérieures.</span><span class="sxs-lookup"><span data-stu-id="f0040-186">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="f0040-187">Uniquement un sous-ensemble des fonctions disponibles pour les tableaux unidimensionnels est également disponible pour les tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="f0040-187">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="f0040-188">Pour plus d’informations, consultez [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), et [ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="f0040-188">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="f0040-189">Le découpage de tableau et les tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="f0040-189">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="f0040-190">Dans un tableau à deux dimensions (matrice), vous pouvez extraire une matrice sous-chemin en spécifiant des plages et à l’aide d’un caractère générique (`*`) pour spécifier des lignes entières ou des colonnes.</span><span class="sxs-lookup"><span data-stu-id="f0040-190">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="f0040-191">À compter de F # 3.1, vous pouvez décomposer un tableau multidimensionnel sous-tableaux de la dimension égale ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="f0040-191">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="f0040-192">Par exemple, vous pouvez obtenir un vecteur à partir d’une matrice en spécifiant une seule ligne ou colonne.</span><span class="sxs-lookup"><span data-stu-id="f0040-192">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="f0040-193">Vous pouvez utiliser cette syntaxe pour les types qui implémentent les opérateurs d’accès élément et d’une surcharge de découpage `GetSlice` méthodes.</span><span class="sxs-lookup"><span data-stu-id="f0040-193">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="f0040-194">Par exemple, le code suivant crée un type de matrice qui encapsule le tableau 2D F #, implémente une propriété d’élément pour prendre en charge l’indexation de tableau et trois versions de `GetSlice`.</span><span class="sxs-lookup"><span data-stu-id="f0040-194">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="f0040-195">Si vous pouvez utiliser ce code en tant que modèle pour vos types de matrice, vous pouvez utiliser toutes les opérations de découpage décrites dans cette section.</span><span class="sxs-lookup"><span data-stu-id="f0040-195">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish = 
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="f0040-196">Fonctions booléennes sur les tableaux</span><span class="sxs-lookup"><span data-stu-id="f0040-196">Boolean Functions on Arrays</span></span>

<span data-ttu-id="f0040-197">Les fonctions [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) et [ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) tester des éléments dans un ou deux tableaux, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f0040-197">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="f0040-198">Ces fonctions acceptent une fonction de test et de retour `true` s’il existe un élément (ou des paires d’éléments pour `Array.exists2`) qui satisfait la condition.</span><span class="sxs-lookup"><span data-stu-id="f0040-198">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="f0040-199">Le code suivant illustre l’utilisation de `Array.exists` et `Array.exists2`.</span><span class="sxs-lookup"><span data-stu-id="f0040-199">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="f0040-200">Dans ces exemples, les nouvelles fonctions sont créées en appliquant un des arguments, dans ces cas, l’argument de fonction uniquement.</span><span class="sxs-lookup"><span data-stu-id="f0040-200">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="f0040-201">La sortie du code précédent est comme suit.</span><span class="sxs-lookup"><span data-stu-id="f0040-201">The output of the preceding code is as follows.</span></span>

```
true
false
false
true
```

<span data-ttu-id="f0040-202">De même, la fonction [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) teste un tableau pour déterminer si chaque élément satisfait à une condition booléenne.</span><span class="sxs-lookup"><span data-stu-id="f0040-202">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="f0040-203">La variation [ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) produit la même chose à l’aide d’une fonction booléenne qui implique les éléments de deux tableaux de longueur égale.</span><span class="sxs-lookup"><span data-stu-id="f0040-203">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="f0040-204">Le code suivant illustre l’utilisation de ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="f0040-204">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="f0040-205">Le résultat de ces exemples est comme suit.</span><span class="sxs-lookup"><span data-stu-id="f0040-205">The output for these examples is as follows.</span></span>

```
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="f0040-206">Recherche dans les tableaux</span><span class="sxs-lookup"><span data-stu-id="f0040-206">Searching Arrays</span></span>

<span data-ttu-id="f0040-207">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)prend une fonction booléenne et retourne le premier élément pour lequel la fonction retourne `true`, ou déclenche un <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> si aucun élément qui satisfait la condition n’a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="f0040-207">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="f0040-208">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)est semblable à `Array.find`, sauf qu’il retourne l’index de l’élément au lieu de l’élément lui-même.</span><span class="sxs-lookup"><span data-stu-id="f0040-208">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="f0040-209">Le code suivant utilise `Array.find` et `Array.findIndex` pour trouver un nombre qui est un carré et un cube parfait.</span><span class="sxs-lookup"><span data-stu-id="f0040-209">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="f0040-210">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="f0040-210">The output is as follows.</span></span>

```
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="f0040-211">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)est semblable à `Array.find`, sauf que son résultat est un type d’option, et elle retourne `None` si aucun élément n’est trouvé.</span><span class="sxs-lookup"><span data-stu-id="f0040-211">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="f0040-212">`Array.tryFind`doit être utilisé à la place de `Array.find` lorsque vous ne connaissez pas si un élément correspondant est dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-212">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="f0040-213">De même, [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) est similaire à [ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) , sauf que le type d’option est la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="f0040-213">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="f0040-214">Si aucun élément n’est trouvé, l’option est `None`.</span><span class="sxs-lookup"><span data-stu-id="f0040-214">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="f0040-215">Le code suivant montre l'utilisation de `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="f0040-215">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="f0040-216">Ce code varie selon le code précédent.</span><span class="sxs-lookup"><span data-stu-id="f0040-216">This code depends on the previous code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="f0040-217">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="f0040-217">The output is as follows.</span></span>

```
Found an element: 1
Found an element: 729
```

<span data-ttu-id="f0040-218">Utilisez [ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) lorsque vous devez transformer un élément en plus de la trouver.</span><span class="sxs-lookup"><span data-stu-id="f0040-218">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="f0040-219">Le résultat est le premier élément pour lequel la fonction retourne l’élément transformé comme valeur d’option, ou `None` si aucun élément correspondant n’est trouvé.</span><span class="sxs-lookup"><span data-stu-id="f0040-219">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="f0040-220">Le code suivant illustre l'utilisation de `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="f0040-220">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="f0040-221">Dans ce cas, au lieu d’une expression lambda, plusieurs fonctions d’assistance locales sont définies pour simplifier le code.</span><span class="sxs-lookup"><span data-stu-id="f0040-221">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="f0040-222">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="f0040-222">The output is as follows.</span></span>

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="f0040-223">Effectuer des calculs sur des tableaux</span><span class="sxs-lookup"><span data-stu-id="f0040-223">Performing Computations on Arrays</span></span>

<span data-ttu-id="f0040-224">Le [ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) fonction retourne la moyenne de chaque élément dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-224">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="f0040-225">Il est limité aux types d’éléments qui prennent en charge la division exacte par un entier, ce qui inclut les types virgule flottante, mais pas les types intégraux.</span><span class="sxs-lookup"><span data-stu-id="f0040-225">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="f0040-226">Le [ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) fonction retourne la moyenne des résultats de l’appel d’une fonction sur chaque élément.</span><span class="sxs-lookup"><span data-stu-id="f0040-226">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="f0040-227">Pour un tableau de type intégral, vous pouvez utiliser `Array.averageBy` et que la fonction convertisse chaque élément flottante type pour le calcul de point.</span><span class="sxs-lookup"><span data-stu-id="f0040-227">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="f0040-228">Utilisez [ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) ou [ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) pour obtenir l’élément minimale ou maximale, si le type d’élément prend en charge.</span><span class="sxs-lookup"><span data-stu-id="f0040-228">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="f0040-229">De même, [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) et [ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) permettent à une fonction à exécuter tout d’abord, par exemple, pour transformer un type qui prend en charge la comparaison.</span><span class="sxs-lookup"><span data-stu-id="f0040-229">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="f0040-230">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)Ajoute les éléments d’un tableau, et [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) appelle une fonction sur chaque élément et additionne les résultats.</span><span class="sxs-lookup"><span data-stu-id="f0040-230">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="f0040-231">Pour exécuter une fonction sur chaque élément dans un tableau sans stocker les valeurs de retour, utilisez [ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span><span class="sxs-lookup"><span data-stu-id="f0040-231">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="f0040-232">Pour une fonction qui implique deux tableaux de longueur égale, utilisez [ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span><span class="sxs-lookup"><span data-stu-id="f0040-232">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="f0040-233">Si vous devez également garder un tableau des résultats de la fonction, utilisez [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) ou [ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), qui fonctionne sur deux tableaux à la fois.</span><span class="sxs-lookup"><span data-stu-id="f0040-233">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="f0040-234">Les variantes [ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) et [ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) permettre à l’index de l’élément à être impliqué dans le calcul ; vaut également pour [ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) et [ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span><span class="sxs-lookup"><span data-stu-id="f0040-234">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="f0040-235">Les fonctions [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [ `Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), et [ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) exécutent des algorithmes qui impliquent tous les éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-235">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="f0040-236">De même, les variations [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) et [ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) effectuer des calculs sur deux tableaux.</span><span class="sxs-lookup"><span data-stu-id="f0040-236">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="f0040-237">Ces fonctions pour effectuer des calculs correspondent aux fonctions du même nom dans la [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="f0040-237">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="f0040-238">Pour obtenir des exemples, consultez [répertorie](lists.md).</span><span class="sxs-lookup"><span data-stu-id="f0040-238">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="f0040-239">Modification de tableaux</span><span class="sxs-lookup"><span data-stu-id="f0040-239">Modifying Arrays</span></span>

<span data-ttu-id="f0040-240">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)définit un élément à une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f0040-240">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="f0040-241">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)définit une plage d’éléments dans un tableau à une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f0040-241">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="f0040-242">Le code suivant fournit un exemple de `Array.fill`.</span><span class="sxs-lookup"><span data-stu-id="f0040-242">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="f0040-243">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="f0040-243">The output is as follows.</span></span>

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="f0040-244">Vous pouvez utiliser [ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) pour copier une sous-section d’un tableau à un autre tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-244">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="f0040-245">Conversion vers et depuis d’autres Types</span><span class="sxs-lookup"><span data-stu-id="f0040-245">Converting to and from Other Types</span></span>

<span data-ttu-id="f0040-246">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)Crée un tableau à partir d’une liste.</span><span class="sxs-lookup"><span data-stu-id="f0040-246">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="f0040-247">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)Crée un tableau à partir d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="f0040-247">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="f0040-248">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)et [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convertir ces autres types de collection à partir du type de tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-248">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="f0040-249">Tri de tableaux</span><span class="sxs-lookup"><span data-stu-id="f0040-249">Sorting Arrays</span></span>

<span data-ttu-id="f0040-250">Utilisez [ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) pour trier un tableau à l’aide de la fonction de comparaison générique.</span><span class="sxs-lookup"><span data-stu-id="f0040-250">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="f0040-251">Utilisez [ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) pour spécifier une fonction qui génère une valeur, appelé un *clé*, pour trier à l’aide de la fonction de comparaison générique sur la clé.</span><span class="sxs-lookup"><span data-stu-id="f0040-251">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="f0040-252">Utilisez [ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) si vous souhaitez fournir une fonction de comparaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f0040-252">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="f0040-253">`Array.sort`, `Array.sortBy`, et `Array.sortWith` retournent toutes le tableau trié comme nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="f0040-253">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="f0040-254">Les variantes [ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), et [ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modifient le tableau existant au lieu de retourner un nouveau.</span><span class="sxs-lookup"><span data-stu-id="f0040-254">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="f0040-255">Tableaux et Tuples</span><span class="sxs-lookup"><span data-stu-id="f0040-255">Arrays and Tuples</span></span>

<span data-ttu-id="f0040-256">Les fonctions [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) et [ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convertissent des tableaux de paires de tuples en tuples de tableaux et vice versa.</span><span class="sxs-lookup"><span data-stu-id="f0040-256">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="f0040-257">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)et [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) sont similaires à ceci près qu’ils fonctionnent avec des tuples de trois éléments ou des tuples de trois tableaux.</span><span class="sxs-lookup"><span data-stu-id="f0040-257">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="f0040-258">Calculs parallèles sur les tableaux</span><span class="sxs-lookup"><span data-stu-id="f0040-258">Parallel Computations on Arrays</span></span>

<span data-ttu-id="f0040-259">Le module [ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contient des fonctions permettant d’effectuer les calculs parallèles sur les tableaux.</span><span class="sxs-lookup"><span data-stu-id="f0040-259">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="f0040-260">Ce module n’est pas disponible dans les applications qui ciblent des versions du .NET Framework antérieures à la version 4.</span><span class="sxs-lookup"><span data-stu-id="f0040-260">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0040-261">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0040-261">See Also</span></span>
[<span data-ttu-id="f0040-262">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="f0040-262">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f0040-263">F #; Types de</span><span class="sxs-lookup"><span data-stu-id="f0040-263">F#; Types</span></span>](fsharp-types.md)
