---
title: "Paramètres de type résolus statiquement (F#)"
description: "Découvrez comment utiliser F # paramètre de type résolus statiquement, qui est remplacé par un type réel au moment de la compilation plutôt qu’au moment de l’exécution."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b3797415-3e49-4f8a-a8ee-fa614c5721aa
ms.openlocfilehash: 88b4590a4323e75949c1915503b51793283792de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="80bd3-104">Paramètres de type résolus statiquement</span><span class="sxs-lookup"><span data-stu-id="80bd3-104">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="80bd3-105">A *paramètre de type résolus statiquement* est un paramètre de type qui est remplacé par un type réel au moment de la compilation plutôt qu’au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="80bd3-105">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="80bd3-106">Elles sont précédées par un signe insertion (^).</span><span class="sxs-lookup"><span data-stu-id="80bd3-106">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="80bd3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80bd3-107">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="80bd3-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="80bd3-108">Remarks</span></span>
<span data-ttu-id="80bd3-109">Dans le langage F #, il existe deux types distincts de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="80bd3-109">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="80bd3-110">Le premier type est le paramètre de type générique standard.</span><span class="sxs-lookup"><span data-stu-id="80bd3-110">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="80bd3-111">Elles sont indiquées par une apostrophe ('), comme dans `'T` et `'U`.</span><span class="sxs-lookup"><span data-stu-id="80bd3-111">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="80bd3-112">Ils sont équivalents aux paramètres de type générique dans d’autres langages .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="80bd3-112">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="80bd3-113">L’autre type est résolu statiquement et est indiqué par un symbole de point d’insertion, comme dans `^T` et `^U`.</span><span class="sxs-lookup"><span data-stu-id="80bd3-113">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="80bd3-114">Paramètres de type résolus statiquement sont essentiellement utiles conjointement aux contraintes de membre, qui sont des contraintes qui vous permettent de spécifier qu’un argument de type doit avoir un membre particulier ou les membres pour pouvoir être utilisé.</span><span class="sxs-lookup"><span data-stu-id="80bd3-114">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="80bd3-115">Il n’existe aucun moyen pour créer ce type de contrainte à l’aide d’un paramètre de type générique normal.</span><span class="sxs-lookup"><span data-stu-id="80bd3-115">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="80bd3-116">Le tableau suivant récapitule les similitudes et les différences entre les deux types de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="80bd3-116">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="80bd3-117">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="80bd3-117">Feature</span></span>|<span data-ttu-id="80bd3-118">Générique</span><span class="sxs-lookup"><span data-stu-id="80bd3-118">Generic</span></span>|<span data-ttu-id="80bd3-119">Résolus statiquement</span><span class="sxs-lookup"><span data-stu-id="80bd3-119">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="80bd3-120">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80bd3-120">Syntax</span></span>|<span data-ttu-id="80bd3-121">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="80bd3-121">`'T`, `'U`</span></span>|<span data-ttu-id="80bd3-122">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="80bd3-122">`^T`, `^U`</span></span>|
|<span data-ttu-id="80bd3-123">Temps de résolution</span><span class="sxs-lookup"><span data-stu-id="80bd3-123">Resolution time</span></span>|<span data-ttu-id="80bd3-124">Au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="80bd3-124">Run time</span></span>|<span data-ttu-id="80bd3-125">Moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="80bd3-125">Compile time</span></span>|
|<span data-ttu-id="80bd3-126">Contraintes de membre</span><span class="sxs-lookup"><span data-stu-id="80bd3-126">Member constraints</span></span>|<span data-ttu-id="80bd3-127">Ne peut pas être utilisé avec les contraintes de membre.</span><span class="sxs-lookup"><span data-stu-id="80bd3-127">Cannot be used with member constraints.</span></span>|<span data-ttu-id="80bd3-128">Peut être utilisé avec les contraintes de membre.</span><span class="sxs-lookup"><span data-stu-id="80bd3-128">Can be used with member constraints.</span></span>|
|<span data-ttu-id="80bd3-129">Génération de code</span><span class="sxs-lookup"><span data-stu-id="80bd3-129">Code generation</span></span>|<span data-ttu-id="80bd3-130">Un type (ou une méthode) avec des paramètres de type générique standard entraîne la génération d’un type générique unique ou une méthode.</span><span class="sxs-lookup"><span data-stu-id="80bd3-130">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="80bd3-131">Plusieurs instanciations de types et méthodes sont générées, un pour chaque type qui est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="80bd3-131">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="80bd3-132">Utiliser avec des types</span><span class="sxs-lookup"><span data-stu-id="80bd3-132">Use with types</span></span>|<span data-ttu-id="80bd3-133">Peut être utilisé sur les types.</span><span class="sxs-lookup"><span data-stu-id="80bd3-133">Can be used on types.</span></span>|<span data-ttu-id="80bd3-134">Ne peut pas être utilisé sur les types.</span><span class="sxs-lookup"><span data-stu-id="80bd3-134">Cannot be used on types.</span></span>|
|<span data-ttu-id="80bd3-135">Utiliser avec les fonctions inline</span><span class="sxs-lookup"><span data-stu-id="80bd3-135">Use with inline functions</span></span>|<span data-ttu-id="80bd3-136">Non.</span><span class="sxs-lookup"><span data-stu-id="80bd3-136">No.</span></span> <span data-ttu-id="80bd3-137">Une fonction inline ne peut pas être paramétrée avec un paramètre de type générique standard.</span><span class="sxs-lookup"><span data-stu-id="80bd3-137">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="80bd3-138">Oui.</span><span class="sxs-lookup"><span data-stu-id="80bd3-138">Yes.</span></span> <span data-ttu-id="80bd3-139">Paramètres de type résolus statiquement ne peut pas être utilisés sur les fonctions ou méthodes qui ne sont pas inline.</span><span class="sxs-lookup"><span data-stu-id="80bd3-139">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="80bd3-140">Nombreuses fonctions F # core library, notamment les opérateurs, ont des paramètres de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="80bd3-140">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="80bd3-141">Ces fonctions et opérateurs sont inline et entraînent la génération de code efficace pour les calculs numériques.</span><span class="sxs-lookup"><span data-stu-id="80bd3-141">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="80bd3-142">Méthodes inline et les fonctions qui utilisent des opérateurs, ou utilisent d’autres fonctions qui ont des paramètres de type résolus statiquement peuvent également utiliser des paramètres de type résolus statiquement proprement dits.</span><span class="sxs-lookup"><span data-stu-id="80bd3-142">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="80bd3-143">Souvent, l’inférence de type déduit ces fonctions inline ont des paramètres de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="80bd3-143">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="80bd3-144">L’exemple suivant illustre une définition d’opérateur est déduite comme ayant un paramètre de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="80bd3-144">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="80bd3-145">Le type résolu de `(+@)` est basée sur l’utilisation des deux `(+)` et `(*)`, à la fois qui amènent l’inférence de type déduire les contraintes de membre sur les paramètres de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="80bd3-145">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="80bd3-146">Le type résolu, comme indiqué dans l’interpréteur F #, est comme suit.</span><span class="sxs-lookup"><span data-stu-id="80bd3-146">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member (+) : ^a * ^b -> ^d) and
(^a or ^c) : (static member (+) : ^a * ^c -> ^b)
```

<span data-ttu-id="80bd3-147">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="80bd3-147">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="80bd3-148">À compter de F # 4.1, vous pouvez également spécifier les noms de type concret dans les signatures de paramètres de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="80bd3-148">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="80bd3-149">Dans les versions précédentes de la langue, le nom de type peut effectivement être déduit par le compilateur, mais n’a pas réellement être spécifié dans la signature.</span><span class="sxs-lookup"><span data-stu-id="80bd3-149">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="80bd3-150">À compter de F # 4.1, vous pouvez également spécifier des noms de type concret dans les signatures de paramètres de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="80bd3-150">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="80bd3-151">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="80bd3-151">Here's an example:</span></span>

```fsharp
type CFunctor() = 
      static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
      static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

      // default implementation of replace
      static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

      // call overridden replace if present
      static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
      ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a><span data-ttu-id="80bd3-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80bd3-152">See Also</span></span>
[<span data-ttu-id="80bd3-153">Génériques</span><span class="sxs-lookup"><span data-stu-id="80bd3-153">Generics</span></span>](index.md)

[<span data-ttu-id="80bd3-154">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="80bd3-154">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="80bd3-155">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="80bd3-155">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="80bd3-156">Contraintes</span><span class="sxs-lookup"><span data-stu-id="80bd3-156">Constraints</span></span>](constraints.md)

[<span data-ttu-id="80bd3-157">Fonctions inline</span><span class="sxs-lookup"><span data-stu-id="80bd3-157">Inline Functions</span></span>](../functions/inline-functions.md)
