---
title: "Inférence de type (F#)"
description: "Découvrez comment le compilateur F # déduit les types de valeurs, variables, paramètres et valeurs de retour."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2d5fa4b1-732a-4d71-a62d-07f7ee79fe06
ms.openlocfilehash: c23954c0a0828cc7d2aae0553d37d5ee1dfbe152
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-inference"></a><span data-ttu-id="d421c-104">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="d421c-104">Type Inference</span></span>

<span data-ttu-id="d421c-105">Cette rubrique décrit comment le compilateur F # déduit les types de valeurs, variables, paramètres et valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="d421c-105">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="d421c-106">En général l’inférence de type</span><span class="sxs-lookup"><span data-stu-id="d421c-106">Type Inference in General</span></span>
<span data-ttu-id="d421c-107">L’idée de l’inférence de type est que vous n’avez pas à spécifier les types de constructions F #, sauf lorsque le compilateur ne peut pas déduire ait le type.</span><span class="sxs-lookup"><span data-stu-id="d421c-107">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="d421c-108">Omettre les informations de type explicite ne signifie pas que F # est un langage typé dynamiquement ou que les valeurs en F # sont faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="d421c-108">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="d421c-109">F # est un langage typé statiquement, ce qui signifie que le compilateur déduit un type exact pour chaque construction lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d421c-109">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="d421c-110">S’il n’est pas suffisamment d’informations pour le compilateur déduire les types de chaque construction, vous devez fournir les informations de type supplémentaires, généralement en ajoutant des annotations de type explicite quelque part dans le code.</span><span class="sxs-lookup"><span data-stu-id="d421c-110">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>


## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="d421c-111">Inférence de paramètre et Types de retour</span><span class="sxs-lookup"><span data-stu-id="d421c-111">Inference of Parameter and Return Types</span></span>
<span data-ttu-id="d421c-112">Dans une liste de paramètres, il est inutile de spécifier le type de chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="d421c-112">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="d421c-113">Pourtant, F # est un langage typé statiquement et par conséquent, chaque valeur et chaque expression ont un type défini au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d421c-113">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="d421c-114">Pour les types que vous ne spécifiez pas explicitement, le compilateur déduit le type en fonction du contexte.</span><span class="sxs-lookup"><span data-stu-id="d421c-114">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="d421c-115">Si le type n’est pas un spécifié dans le cas contraire, il est déduit générique.</span><span class="sxs-lookup"><span data-stu-id="d421c-115">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="d421c-116">Si le code utilise une valeur de façon incohérente, de sorte qu’il n’existe pas d’une seule type inféré satisfaisant à toutes les utilisations d’une valeur, que le compilateur signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="d421c-116">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="d421c-117">Le type de retour d’une fonction est déterminé par le type de la dernière expression dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="d421c-117">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="d421c-118">Par exemple, dans le code suivant, les types de paramètres `a` et `b` et le type de retour sont déduits pour être `int` , car le littéral `100` est de type `int`.</span><span class="sxs-lookup"><span data-stu-id="d421c-118">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="d421c-119">Vous pouvez influencer l’inférence de type en modifiant les littéraux.</span><span class="sxs-lookup"><span data-stu-id="d421c-119">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="d421c-120">Si vous effectuez la `100` un `uint32` en ajoutant le suffixe `u`, les types de `a`, `b`, et la valeur de retour sont déduits pour être `uint32`.</span><span class="sxs-lookup"><span data-stu-id="d421c-120">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="d421c-121">Vous pouvez également influencer l’inférence de type à l’aide d’autres constructions qui impliquent des restrictions sur le type, telles que les fonctions et méthodes qui fonctionnent avec un type particulier.</span><span class="sxs-lookup"><span data-stu-id="d421c-121">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="d421c-122">En outre, vous pouvez appliquer des annotations de type explicite pour les paramètres de fonction ou une méthode ou à des variables dans les expressions, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="d421c-122">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="d421c-123">Erreurs survenir si les conflits se produisent entre des contraintes différentes.</span><span class="sxs-lookup"><span data-stu-id="d421c-123">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="d421c-124">Vous pouvez également spécifier explicitement la valeur de retour d’une fonction en fournissant une annotation de type une fois tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="d421c-124">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="d421c-125">Un cas courant où une annotation de type est utile sur un paramètre est lorsque le paramètre est un type d’objet et que vous souhaitez utiliser un membre.</span><span class="sxs-lookup"><span data-stu-id="d421c-125">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a><span data-ttu-id="d421c-126">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="d421c-126">Automatic Generalization</span></span>
<span data-ttu-id="d421c-127">Si le code de fonction n’est pas dépendant du type d’un paramètre, le compilateur considère que le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="d421c-127">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="d421c-128">Il s’agit *généralisation automatique*, et il peut être très utile pour écrire du code générique sans augmenter la complexité.</span><span class="sxs-lookup"><span data-stu-id="d421c-128">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="d421c-129">Par exemple, la fonction suivante combine deux paramètres de n’importe quel type dans un tuple.</span><span class="sxs-lookup"><span data-stu-id="d421c-129">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="d421c-130">Le type est déduit</span><span class="sxs-lookup"><span data-stu-id="d421c-130">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="d421c-131">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d421c-131">Additional Information</span></span>
<span data-ttu-id="d421c-132">L’inférence de type est décrite plus en détail dans la spécification du langage F #.</span><span class="sxs-lookup"><span data-stu-id="d421c-132">Type inference is described in more detail in the F# Language Specification.</span></span>


## <a name="see-also"></a><span data-ttu-id="d421c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d421c-133">See Also</span></span>
[<span data-ttu-id="d421c-134">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="d421c-134">Automatic Generalization</span></span>](generics/automatic-generalization.md)
