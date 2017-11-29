---
title: "Généralisation automatique (F#)"
description: "Découvrez comment F # généralise automatiquement les arguments et les types de fonctions afin qu’ils fonctionnent avec plusieurs types lorsque cela est possible."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 14a3554c-3fad-4eba-a93d-8ba07d1245b4
ms.openlocfilehash: d60831084cef76ce29f64322362b4920520f71d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="automatic-generalization"></a><span data-ttu-id="379d9-104">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="379d9-104">Automatic Generalization</span></span>

<span data-ttu-id="379d9-105">F # utilise l’inférence de type à évaluer les types de fonctions et d’expressions.</span><span class="sxs-lookup"><span data-stu-id="379d9-105">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="379d9-106">Cette rubrique décrit comment F # généralise automatiquement les arguments et les types de fonctions afin qu’ils fonctionnent avec plusieurs types lorsque cela est possible.</span><span class="sxs-lookup"><span data-stu-id="379d9-106">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>


## <a name="automatic-generalization"></a><span data-ttu-id="379d9-107">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="379d9-107">Automatic Generalization</span></span>
<span data-ttu-id="379d9-108">Le compilateur F #, lorsqu’elle effectue l’inférence de type sur une fonction, détermine si un paramètre donné peut être générique.</span><span class="sxs-lookup"><span data-stu-id="379d9-108">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="379d9-109">Le compilateur examine chaque paramètre et détermine si la fonction a une dépendance sur le type spécifique de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="379d9-109">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="379d9-110">Si elle n’est pas le cas, le type est déduit générique.</span><span class="sxs-lookup"><span data-stu-id="379d9-110">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="379d9-111">L’exemple de code suivant illustre une fonction que le compilateur déduit pour être générique.</span><span class="sxs-lookup"><span data-stu-id="379d9-111">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="379d9-112">Le type est déduit que `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="379d9-112">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="379d9-113">Le type indique qu’il s’agit d’une fonction qui accepte deux arguments du même type inconnu et retourne une valeur du même type.</span><span class="sxs-lookup"><span data-stu-id="379d9-113">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="379d9-114">Une des raisons qui la fonction précédente peut être générique est que la plus grande-que l’opérateur (`>`) est lui-même générique.</span><span class="sxs-lookup"><span data-stu-id="379d9-114">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="379d9-115">La plus grande-que l’opérateur a la signature `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="379d9-115">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="379d9-116">Tous les opérateurs ne sont génériques, et si le code dans une fonction utilise un type de paramètre avec une fonction non générique ou un opérateur, ce type de paramètre ne peut pas être généralisé.</span><span class="sxs-lookup"><span data-stu-id="379d9-116">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="379d9-117">Étant donné que `max` est générique, il peut être utilisé avec des types tels que `int`, `float`, et ainsi de suite, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="379d9-117">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="379d9-118">Toutefois, les deux arguments doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="379d9-118">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="379d9-119">La signature est `'a -> 'a -> 'a`, et non `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="379d9-119">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="379d9-120">Par conséquent, le code suivant génère une erreur car les types ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="379d9-120">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="379d9-121">Le `max` fonctionne également avec tout type qui prend en charge la plus grande-que l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="379d9-121">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="379d9-122">Par conséquent, vous pourriez également l’utiliser sur une chaîne, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="379d9-122">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a><span data-ttu-id="379d9-123">Restriction de valeur</span><span class="sxs-lookup"><span data-stu-id="379d9-123">Value Restriction</span></span>
<span data-ttu-id="379d9-124">Le compilateur effectue la généralisation automatique uniquement sur les définitions de fonction complètes qui ont des arguments explicites et sur des valeurs immuables simples.</span><span class="sxs-lookup"><span data-stu-id="379d9-124">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="379d9-125">Cela signifie que le compilateur émet une erreur si vous essayez de compiler le code qui n’est pas suffisamment contraint à être un type spécifique, mais est également pas être transposable.</span><span class="sxs-lookup"><span data-stu-id="379d9-125">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="379d9-126">Pour résoudre ce problème, le message d’erreur fait référence à cette restriction sur la généralisation automatique pour les valeurs que le *valeur restriction*.</span><span class="sxs-lookup"><span data-stu-id="379d9-126">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="379d9-127">En règle générale, l’erreur de restriction de valeur se produit lorsque vous le souhaitez une construction générique, mais le compilateur dispose d’informations suffisantes pour généraliser, ou vous omettez involontairement des informations de type suffisantes dans une construction non générique.</span><span class="sxs-lookup"><span data-stu-id="379d9-127">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="379d9-128">La solution à l’erreur de restriction de valeur est de fournir des informations plus explicites pour mieux contraindre le problème d’inférence de type, de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="379d9-128">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>


- <span data-ttu-id="379d9-129">Contraindre un type non générique en ajoutant une annotation de type explicite à une valeur ou un paramètre.</span><span class="sxs-lookup"><span data-stu-id="379d9-129">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="379d9-130">Si le problème utilise une construction non généralisable pour définir une fonction générique, comme une composition de fonction ou appliqués incomplètement des arguments de fonction curryfiés, essayez de réécrire la fonction comme une définition de fonction ordinaire.</span><span class="sxs-lookup"><span data-stu-id="379d9-130">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="379d9-131">Si le problème est une expression qui est trop complexe pour être généralisée, faites-en une fonction en ajoutant un paramètre supplémentaire inutilisé.</span><span class="sxs-lookup"><span data-stu-id="379d9-131">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="379d9-132">Ajouter des paramètres de type générique explicites.</span><span class="sxs-lookup"><span data-stu-id="379d9-132">Add explicit generic type parameters.</span></span> <span data-ttu-id="379d9-133">Cette option est rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="379d9-133">This option is rarely used.</span></span>

- <span data-ttu-id="379d9-134">Les exemples de code suivants illustrent chacun de ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="379d9-134">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="379d9-135">Cas 1 : Expression trop complexe.</span><span class="sxs-lookup"><span data-stu-id="379d9-135">Case 1: Too complex an expression.</span></span> <span data-ttu-id="379d9-136">Dans cet exemple, la liste `counter` est destinée à être `int option ref`, mais il n’est pas défini comme une valeur immuable simple.</span><span class="sxs-lookup"><span data-stu-id="379d9-136">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="379d9-137">Cas 2 : Utilisation d’une construction non généralisable pour définir une fonction générique.</span><span class="sxs-lookup"><span data-stu-id="379d9-137">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="379d9-138">Dans cet exemple, la construction est non généralisable, car il implique l’application partielle d’arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="379d9-138">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="379d9-139">Cas 3 : Ajout d’un paramètre supplémentaire inutilisé.</span><span class="sxs-lookup"><span data-stu-id="379d9-139">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="379d9-140">Étant donné que cette expression n’est pas suffisamment simple pour la généralisation, le compilateur émet l’erreur de restriction de valeur.</span><span class="sxs-lookup"><span data-stu-id="379d9-140">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="379d9-141">Cas n° 4 : Ajout type de paramètres.</span><span class="sxs-lookup"><span data-stu-id="379d9-141">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="379d9-142">Dans le dernier cas, la valeur devient une fonction de type qui peut être utilisée pour créer des valeurs de différents types, par exemple comme suit :</span><span class="sxs-lookup"><span data-stu-id="379d9-142">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="379d9-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="379d9-143">See Also</span></span>
[<span data-ttu-id="379d9-144">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="379d9-144">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="379d9-145">Génériques</span><span class="sxs-lookup"><span data-stu-id="379d9-145">Generics</span></span>](index.md)

[<span data-ttu-id="379d9-146">Paramètres de type résolus statiquement</span><span class="sxs-lookup"><span data-stu-id="379d9-146">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)

[<span data-ttu-id="379d9-147">Contraintes</span><span class="sxs-lookup"><span data-stu-id="379d9-147">Constraints</span></span>](constraints.md)

