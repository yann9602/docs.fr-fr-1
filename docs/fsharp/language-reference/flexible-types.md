---
title: Types flexibles (F#)
description: "Découvrez comment utiliser F # annotation de type flexible, ce qui indique qu’un paramètre, une variable ou une valeur a un type qui est compatible avec un type spécifié."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c8b510f2-3405-4cc9-b55b-e47b35e2b15b
ms.openlocfilehash: 7c5e4eb97791b9c6c56fe2847755866e8240e038
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="flexible-types"></a><span data-ttu-id="dc248-104">Types flexibles</span><span class="sxs-lookup"><span data-stu-id="dc248-104">Flexible Types</span></span>

<span data-ttu-id="dc248-105">A *annotation de type flexible* indique qu’un paramètre, une variable ou une valeur a un type qui est compatible avec un type spécifié, où la compatibilité est déterminée par la position dans une hiérarchie orientée objet de classes ou des interfaces.</span><span class="sxs-lookup"><span data-stu-id="dc248-105">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="dc248-106">Types flexibles sont particulièrement utiles lorsque la conversion automatique en types de niveau supérieurs dans la hiérarchie des types ne se produit pas, mais vous souhaitez activer votre fonctionnalité de fonctionner avec n’importe quel type dans la hiérarchie ou n’importe quel type qui implémente une interface.</span><span class="sxs-lookup"><span data-stu-id="dc248-106">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="dc248-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc248-107">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="dc248-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="dc248-108">Remarks</span></span>

<span data-ttu-id="dc248-109">Dans la syntaxe précédente, *type* représente un type de base ou une interface.</span><span class="sxs-lookup"><span data-stu-id="dc248-109">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="dc248-110">Un type flexible équivaut à un type générique qui a une contrainte qui limite les types autorisés en types compatibles avec le type de base ou interface.</span><span class="sxs-lookup"><span data-stu-id="dc248-110">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="dc248-111">Autrement dit, les deux lignes de code suivantes sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="dc248-111">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="dc248-112">Types flexibles sont utiles dans plusieurs types de situations.</span><span class="sxs-lookup"><span data-stu-id="dc248-112">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="dc248-113">Par exemple, lorsque vous disposez d’une fonction d’ordre supérieur (une fonction qui accepte une fonction en tant qu’argument), il est souvent utile de disposer de la fonction retourne un type flexible.</span><span class="sxs-lookup"><span data-stu-id="dc248-113">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="dc248-114">Dans l’exemple suivant, l’utilisation d’un type flexible avec un argument de séquence dans `iterate2` permet à la fonction d’ordre supérieure d’utiliser des fonctions qui génèrent des séquences, tableaux, listes et autres types énumérables.</span><span class="sxs-lookup"><span data-stu-id="dc248-114">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="dc248-115">Considérez les deux fonctions suivantes, une retourne une séquence, l’autre qui retourne un type flexible.</span><span class="sxs-lookup"><span data-stu-id="dc248-115">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="dc248-116">Comme autre exemple, prenez le [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) fonction de bibliothèque :</span><span class="sxs-lookup"><span data-stu-id="dc248-116">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="dc248-117">Vous pouvez passer les séquences énumérables suivantes à cette fonction :</span><span class="sxs-lookup"><span data-stu-id="dc248-117">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="dc248-118">Une liste de listes</span><span class="sxs-lookup"><span data-stu-id="dc248-118">A list of lists</span></span>
- <span data-ttu-id="dc248-119">Une liste de tableaux</span><span class="sxs-lookup"><span data-stu-id="dc248-119">A list of arrays</span></span>
- <span data-ttu-id="dc248-120">Un tableau de listes</span><span class="sxs-lookup"><span data-stu-id="dc248-120">An array of lists</span></span>
- <span data-ttu-id="dc248-121">Un tableau de séquences</span><span class="sxs-lookup"><span data-stu-id="dc248-121">An array of sequences</span></span>
- <span data-ttu-id="dc248-122">Toute autre combinaison de séquences énumérables</span><span class="sxs-lookup"><span data-stu-id="dc248-122">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="dc248-123">Le code suivant utilise `Seq.concat` pour montrer les scénarios que vous pouvez prendre en charge à l’aide de types flexibles.</span><span class="sxs-lookup"><span data-stu-id="dc248-123">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="dc248-124">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="dc248-124">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="dc248-125">En F #, comme dans d’autres langages orientés objet, sont les contextes dans lesquels les types dérivés ou les types qui implémentent les interfaces sont converties automatiquement en un type de base ou interface.</span><span class="sxs-lookup"><span data-stu-id="dc248-125">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="dc248-126">Ces conversions automatiques se produisent dans les arguments directs, mais pas lorsque le type est dans une position subordonnée, dans le cadre d’un type plus complexe comme un type de retour d’un type de fonction, ou un argument de type.</span><span class="sxs-lookup"><span data-stu-id="dc248-126">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="dc248-127">Par conséquent, la notation de type flexible est particulièrement utile lorsque le type que vous l’appliquez fait partie d’un type plus complexe.</span><span class="sxs-lookup"><span data-stu-id="dc248-127">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc248-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc248-128">See Also</span></span>

[<span data-ttu-id="dc248-129">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="dc248-129">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="dc248-130">Génériques</span><span class="sxs-lookup"><span data-stu-id="dc248-130">Generics</span></span>](generics/index.md)
