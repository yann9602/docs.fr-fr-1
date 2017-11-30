---
title: Fonctions inline (F#)
description: "Découvrez comment utiliser les fonctions F # inline intégrés directement dans le code appelant."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 0489d411e2754eaab6a10ff0feb4405491b3b511
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2017
---
# <a name="inline-functions"></a><span data-ttu-id="effa6-104">Fonctions inline</span><span class="sxs-lookup"><span data-stu-id="effa6-104">Inline Functions</span></span>

<span data-ttu-id="effa6-105">*Les fonctions inline* sont des fonctions intégrées directement dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="effa6-105">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="effa6-106">À l’aide de fonctions Inline</span><span class="sxs-lookup"><span data-stu-id="effa6-106">Using Inline Functions</span></span>
<span data-ttu-id="effa6-107">Lorsque vous utilisez des paramètres de type statique, toutes les fonctions qui sont paramétrables par des paramètres de type doivent être inline.</span><span class="sxs-lookup"><span data-stu-id="effa6-107">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="effa6-108">Cela garantit que le compilateur peut résoudre ces paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="effa6-108">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="effa6-109">Lorsque vous utilisez des paramètres de type générique ordinaires, il n’existe aucune restriction de ce type.</span><span class="sxs-lookup"><span data-stu-id="effa6-109">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="effa6-110">Autre que l’activation de l’utilisation de contraintes de membre, les fonctions inline peuvent être utiles pour optimiser le code.</span><span class="sxs-lookup"><span data-stu-id="effa6-110">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="effa6-111">Toutefois, les utilisation abusive des fonctions inline peut rendre votre code moins résistant aux modifications apportées aux optimisations du compilateur et l’implémentation des fonctions de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="effa6-111">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="effa6-112">Pour cette raison, évitez d’utiliser des fonctions inline pour l’optimisation, sauf si vous avez tenté de tous les autres techniques d’optimisation.</span><span class="sxs-lookup"><span data-stu-id="effa6-112">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="effa6-113">Rendre une fonction ou une méthode inline peut parfois améliorer les performances, mais qui n’est pas toujours le cas.</span><span class="sxs-lookup"><span data-stu-id="effa6-113">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="effa6-114">Par conséquent, vous devez également utiliser les mesures de performances pour vérifier que la fabrication d’une fonction donnée inline n’a en fait un effet positif.</span><span class="sxs-lookup"><span data-stu-id="effa6-114">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="effa6-115">Le `inline` modificateur peut être appliqué à des fonctions au niveau supérieur, au niveau du module ou au niveau de la méthode dans une classe.</span><span class="sxs-lookup"><span data-stu-id="effa6-115">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="effa6-116">L’exemple de code suivant illustre une fonction inline au niveau supérieur, une méthode d’instance inline et une méthode statique inline.</span><span class="sxs-lookup"><span data-stu-id="effa6-116">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="effa6-117">Les fonctions inline et inférence de Type</span><span class="sxs-lookup"><span data-stu-id="effa6-117">Inline Functions and Type Inference</span></span>
<span data-ttu-id="effa6-118">La présence de `inline` affecte l’inférence de type.</span><span class="sxs-lookup"><span data-stu-id="effa6-118">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="effa6-119">Il s’agit, car les fonctions inline peuvent avoir résolus statiquement des paramètres de type, alors que les fonctions non inline ne peut pas.</span><span class="sxs-lookup"><span data-stu-id="effa6-119">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="effa6-120">L’exemple de code suivant illustre un cas où `inline` est utile parce que vous utilisez une fonction qui a un paramètre de type résolus statiquement, le `float` opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="effa6-120">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="effa6-121">Sans le `inline` modificateur, l’inférence de type force la fonction à prendre un type spécifique, dans ce cas `int`.</span><span class="sxs-lookup"><span data-stu-id="effa6-121">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="effa6-122">Mais avec la `inline` modificateur, la fonction est également déduite comme ayant un paramètre de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="effa6-122">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="effa6-123">Avec la `inline` modificateur, le type est déduit que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="effa6-123">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="effa6-124">Cela signifie que la fonction accepte tout type qui prend en charge une conversion vers **float**.</span><span class="sxs-lookup"><span data-stu-id="effa6-124">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="effa6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="effa6-125">See Also</span></span>
[<span data-ttu-id="effa6-126">Fonctions</span><span class="sxs-lookup"><span data-stu-id="effa6-126">Functions</span></span>](index.md)

[<span data-ttu-id="effa6-127">Contraintes</span><span class="sxs-lookup"><span data-stu-id="effa6-127">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="effa6-128">Paramètres de type résolus statiquement</span><span class="sxs-lookup"><span data-stu-id="effa6-128">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
