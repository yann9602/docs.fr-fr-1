---
title: Calculs tardifs (F#)
description: "Découvrez comment F # tardifs peuvent améliorer les performances de vos applications et bibliothèques."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3499293e-1d53-4b02-b764-f687fbdaa7fe
ms.openlocfilehash: 984c96ab68a8919e2382eefe8260b07f191027dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="lazy-computations"></a><span data-ttu-id="d0d9a-104">Calculs tardifs</span><span class="sxs-lookup"><span data-stu-id="d0d9a-104">Lazy Computations</span></span>

<span data-ttu-id="d0d9a-105">*Calculs tardifs* sont des calculs qui ne sont pas évalués immédiatement, mais sont évaluées à la place lorsque le résultat est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-105">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="d0d9a-106">Cela peut aider à améliorer les performances de votre code.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-106">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0d9a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0d9a-107">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="d0d9a-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="d0d9a-108">Remarks</span></span>

<span data-ttu-id="d0d9a-109">Dans la syntaxe précédente, *expression* est un code qui est évalué uniquement lorsqu’un résultat est requis, et *identificateur* est une valeur qui stocke le résultat.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-109">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="d0d9a-110">La valeur est de type [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), où le type réel qui est utilisé pour `'T` est déterminé à partir du résultat de l’expression.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-110">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="d0d9a-111">Calculs tardifs permettent d’améliorer les performances en limitant l’exécution d’un calcul aux seules situations dans lesquelles un résultat est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-111">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="d0d9a-112">Pour forcer l’exécution du calcul, vous appelez la méthode `Force`.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-112">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="d0d9a-113">`Force`entraîne l’exécution à effectuer qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-113">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="d0d9a-114">Les appels suivants à `Force` le même résultat, mais n’exécutent pas le code de retour.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-114">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="d0d9a-115">Le code suivant illustre l’utilisation du calcul tardif et l’utilisation de `Force`.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-115">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="d0d9a-116">Dans ce code, le type de `result` est `Lazy<int>`et le `Force` méthode retourne un `int`.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-116">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="d0d9a-117">L’évaluation différée, mais pas les `Lazy` type, est également utilisé pour les séquences.</span><span class="sxs-lookup"><span data-stu-id="d0d9a-117">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="d0d9a-118">Pour plus d’informations, consultez [séquences](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="d0d9a-118">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0d9a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0d9a-119">See Also</span></span>

[<span data-ttu-id="d0d9a-120">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="d0d9a-120">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="d0d9a-121">LazyExtensions (module)</span><span class="sxs-lookup"><span data-stu-id="d0d9a-121">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
