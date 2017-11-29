---
title: "Boucles : expression for...in (F#)"
description: "Voir comment la boucle for) (F #... dans l’expression de construction en boucle est utilisée pour itérer sur les correspondances d’un modèle dans une collection énumérable."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f54e3228-4aec-4d0a-ae37-bc3376508284
ms.openlocfilehash: d86aeb3bdd975261e59004d636354a740bd95c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forin-expression"></a><span data-ttu-id="8a681-104">Boucles : expression for...in</span><span class="sxs-lookup"><span data-stu-id="8a681-104">Loops: for...in Expression</span></span>

<span data-ttu-id="8a681-105">Cette construction de bouclage est utilisée pour itérer sur les correspondances d’un modèle dans une collection énumérable comme une expression de plage, séquence, liste, tableau ou autre construction qui prend en charge d’énumération.</span><span class="sxs-lookup"><span data-stu-id="8a681-105">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>


## <a name="syntax"></a><span data-ttu-id="8a681-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a681-106">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="8a681-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="8a681-107">Remarks</span></span>
<span data-ttu-id="8a681-108">Le `for...in` expression peut être comparée à la `for each` instruction dans d’autres langages .NET, car il est utilisé pour effectuer une boucle sur les valeurs d’une collection énumérable.</span><span class="sxs-lookup"><span data-stu-id="8a681-108">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="8a681-109">Toutefois, `for...in` prend également en charge la mise en correspondance sur la collection au lieu de simplement itération sur la collection entière.</span><span class="sxs-lookup"><span data-stu-id="8a681-109">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="8a681-110">L’expression énumérable peut être spécifiée comme une collection énumérable ou, à l’aide de la `..` opérateur, comme une plage sur un type intégral.</span><span class="sxs-lookup"><span data-stu-id="8a681-110">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="8a681-111">Les collections énumérables incluent les listes, séquences, tableaux, jeux, mappages et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8a681-111">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="8a681-112">Tout type qui implémente `System.Collections.IEnumerable` peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="8a681-112">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="8a681-113">Lorsque vous exprimez une plage à l’aide de la `..` (opérateur), vous pouvez utiliser la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="8a681-113">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="8a681-114">*Démarrer* ...</span><span class="sxs-lookup"><span data-stu-id="8a681-114">*start* ..</span></span> <span data-ttu-id="8a681-115">*Terminer*</span><span class="sxs-lookup"><span data-stu-id="8a681-115">*finish*</span></span>

<span data-ttu-id="8a681-116">Vous pouvez également utiliser une version qui inclut un incrément appelé le *ignorer*, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="8a681-116">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="8a681-117">*Démarrer* ...</span><span class="sxs-lookup"><span data-stu-id="8a681-117">*start* ..</span></span> <span data-ttu-id="8a681-118">*Ignorer* ...</span><span class="sxs-lookup"><span data-stu-id="8a681-118">*skip* ..</span></span> <span data-ttu-id="8a681-119">*Terminer*</span><span class="sxs-lookup"><span data-stu-id="8a681-119">*finish*</span></span>

<span data-ttu-id="8a681-120">Lorsque vous utilisez des plages intégrales et une variable de compteur simple comme modèle, le comportement par défaut est pour incrémenter la variable de compteur de 1 à chaque itération, mais si la plage comprend une valeur à ignorer, le compteur est incrémenté par la valeur skip à la place.</span><span class="sxs-lookup"><span data-stu-id="8a681-120">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="8a681-121">Les valeurs correspondantes dans le modèle peuvent également servir dans l’expression de corps.</span><span class="sxs-lookup"><span data-stu-id="8a681-121">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="8a681-122">Les exemples de code suivants illustrent l’utilisation de la `for...in` expression.</span><span class="sxs-lookup"><span data-stu-id="8a681-122">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="8a681-123">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="8a681-123">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="8a681-124">L’exemple suivant montre comment effectuer une boucle sur une séquence et comment utiliser un modèle de tuple au lieu d’une simple variable.</span><span class="sxs-lookup"><span data-stu-id="8a681-124">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="8a681-125">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="8a681-125">The output is as follows.</span></span>

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="8a681-126">L’exemple suivant montre comment effectuer une boucle sur une plage d’entiers simple.</span><span class="sxs-lookup"><span data-stu-id="8a681-126">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="8a681-127">La sortie de function1 est la suivante.</span><span class="sxs-lookup"><span data-stu-id="8a681-127">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="8a681-128">L’exemple suivant montre comment effectuer une boucle sur une plage avec un saut de 2, qui inclut tous les autres éléments de la plage.</span><span class="sxs-lookup"><span data-stu-id="8a681-128">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="8a681-129">La sortie de `function2` est comme suit.</span><span class="sxs-lookup"><span data-stu-id="8a681-129">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="8a681-130">L’exemple suivant montre comment utiliser une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="8a681-130">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="8a681-131">La sortie de `function3` est comme suit.</span><span class="sxs-lookup"><span data-stu-id="8a681-131">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="8a681-132">L’exemple suivant montre comment utiliser une valeur de saut négative pour effectuer une itération inverse.</span><span class="sxs-lookup"><span data-stu-id="8a681-132">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="8a681-133">La sortie de `function4` est comme suit.</span><span class="sxs-lookup"><span data-stu-id="8a681-133">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="8a681-134">Le début et la fin de la plage peuvent également être des expressions, telles que des fonctions, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="8a681-134">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="8a681-135">La sortie de `function5` avec cette entrée est la suivante.</span><span class="sxs-lookup"><span data-stu-id="8a681-135">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="8a681-136">L’exemple suivant illustre l’utilisation d’un caractère générique (_) lorsque l’élément n’est pas nécessaire dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="8a681-136">The next example shows the use of a wildcard character (_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="8a681-137">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="8a681-137">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="8a681-138">`Note`Vous pouvez utiliser `for...in` dans les expressions de séquence et autres expressions de calcul, auquel cas une version personnalisée de la `for...in` expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8a681-138">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="8a681-139">Pour plus d’informations, consultez [séquences](sequences.md), [Workflows asynchrones](asynchronous-workflows.md), et [Expressions de calcul](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8a681-139">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="8a681-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a681-140">See Also</span></span>
[<span data-ttu-id="8a681-141">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="8a681-141">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="8a681-142">Boucles : expression `for...to`</span><span class="sxs-lookup"><span data-stu-id="8a681-142">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

[<span data-ttu-id="8a681-143">Boucles : expression `while...do`</span><span class="sxs-lookup"><span data-stu-id="8a681-143">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
