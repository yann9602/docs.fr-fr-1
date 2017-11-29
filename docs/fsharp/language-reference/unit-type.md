---
title: Type unit (F#)
description: "Découvrez comment le type 'unit' F # est souvent utilisé pour marquer l’emplacement où une valeur est requise par la syntaxe du langage lorsqu’aucune valeur n’est nécessaire ou souhaitée."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: eabbb6d7-80f3-4fa5-80b4-0f48982466a7
ms.openlocfilehash: 60ac08c0e3f8380a8f9dec7a083ede93c68bb0e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="unit-type"></a><span data-ttu-id="fe685-104">Unit, type</span><span class="sxs-lookup"><span data-stu-id="fe685-104">Unit Type</span></span>

<span data-ttu-id="fe685-105">Le `unit` type est un type qui indique l’absence d’une valeur spécifique ; la `unit` type a uniquement une valeur unique, qui agit comme un espace réservé lorsqu’aucune autre valeur n’existe ou n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fe685-105">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>


## <a name="syntax"></a><span data-ttu-id="fe685-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe685-106">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="fe685-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="fe685-107">Remarks</span></span>
<span data-ttu-id="fe685-108">Chaque expression F # doit correspondre à une valeur.</span><span class="sxs-lookup"><span data-stu-id="fe685-108">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="fe685-109">Pour les expressions qui ne génèrent pas d’une valeur qui présente un intérêt, la valeur de type `unit` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="fe685-109">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="fe685-110">Le `unit` type ressemble à la `void` type dans les langages tels que c# et C++.</span><span class="sxs-lookup"><span data-stu-id="fe685-110">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="fe685-111">Le `unit` type a une valeur unique, et qui est indiquée par le jeton `()`.</span><span class="sxs-lookup"><span data-stu-id="fe685-111">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="fe685-112">La valeur de la `unit` type est souvent utilisé dans la programmation F # pour marquer l’emplacement où une valeur est requise par la syntaxe du langage, mais lorsqu’aucune valeur n’est nécessaire ou souhaitée.</span><span class="sxs-lookup"><span data-stu-id="fe685-112">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="fe685-113">Un exemple peut être la valeur de retour d’un `printf` (fonction).</span><span class="sxs-lookup"><span data-stu-id="fe685-113">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="fe685-114">Étant donné que les actions importantes de la `printf` opération se produit dans la fonction, la fonction n’a pas retourner une valeur réelle.</span><span class="sxs-lookup"><span data-stu-id="fe685-114">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="fe685-115">Par conséquent, la valeur de retour est de type `unit`.</span><span class="sxs-lookup"><span data-stu-id="fe685-115">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="fe685-116">Certaines constructions attendent une `unit` valeur.</span><span class="sxs-lookup"><span data-stu-id="fe685-116">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="fe685-117">Par exemple, un `do` liaison ou du code au niveau supérieur d’un module est censé prendre une `unit` valeur.</span><span class="sxs-lookup"><span data-stu-id="fe685-117">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="fe685-118">Le compilateur émet un avertissement quand un `do` liaison ou du code au niveau supérieur d’un module produit un résultat autre que le `unit` valeur qui n’est pas utilisé, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fe685-118">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="fe685-119">Cet avertissement est une caractéristique de la programmation fonctionnelle ; Il n’apparaît pas dans les autres langages de programmation .NET.</span><span class="sxs-lookup"><span data-stu-id="fe685-119">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="fe685-120">Dans un programme purement fonctionnel, dans lequel les fonctions n’ont pas d’effets secondaires, la valeur de retournée finale est le seul résultat d’un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="fe685-120">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="fe685-121">Par conséquent, lorsque le résultat est ignoré, il est une erreur de programmation possible.</span><span class="sxs-lookup"><span data-stu-id="fe685-121">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="fe685-122">Bien que F # n’est pas un langage de programmation purement fonctionnel, il est conseillé de suivre le style de programmation fonctionnelle autant que possible.</span><span class="sxs-lookup"><span data-stu-id="fe685-122">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe685-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe685-123">See Also</span></span>
[<span data-ttu-id="fe685-124">Primitifs</span><span class="sxs-lookup"><span data-stu-id="fe685-124">Primitive</span></span>](primitive-types.md)

[<span data-ttu-id="fe685-125">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="fe685-125">F# Language Reference</span></span>](index.md)
