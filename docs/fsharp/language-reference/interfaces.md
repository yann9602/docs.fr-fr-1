---
title: Interfaces (F#)
description: "Découvrez comment F # Interfaces spécifient des jeux de membres associés qui implémentent des autres classes."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a082459-17d4-45cf-9153-0b7550a154ec
ms.openlocfilehash: d7c95e5f5cc0bc6c7f6393af990427ac491c5b79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a><span data-ttu-id="d8b4f-104">Interfaces</span><span class="sxs-lookup"><span data-stu-id="d8b4f-104">Interfaces</span></span>

<span data-ttu-id="d8b4f-105">*Interfaces* spécifient des jeux de membres connexes que d’autres classes implémentent.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-105">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8b4f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8b4f-106">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a><span data-ttu-id="d8b4f-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="d8b4f-107">Remarks</span></span>
<span data-ttu-id="d8b4f-108">Déclarations d’interface ressemblent aux déclarations de classe, sauf qu’aucun membre n’est implémentées.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-108">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="d8b4f-109">Au lieu de cela, tous les membres sont abstraits, comme indiqué par le mot clé `abstract`.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-109">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="d8b4f-110">Vous ne fournissez pas un corps de méthode pour les méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-110">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="d8b4f-111">Toutefois, vous pouvez fournir une implémentation par défaut en incluant une définition séparée du membre comme une méthode avec le `default` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="d8b4f-111">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="d8b4f-112">Cela équivaut à la création d’une méthode virtuelle dans une classe de base dans d’autres langages .NET.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-112">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="d8b4f-113">Une telle méthode virtuelle peut être substituée dans les classes qui implémentent l’interface.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-113">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="d8b4f-114">Vous pouvez éventuellement donner à chaque paramètre de méthode un nom à l’aide de la syntaxe normale F # :</span><span class="sxs-lookup"><span data-stu-id="d8b4f-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="d8b4f-115">Dans l’exemple ci-dessus `ISprintable` exemple, le `Print` méthode possède un paramètre unique du type `string` portant le nom `format`.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="d8b4f-116">Il existe deux façons d’implémenter des interfaces : à l’aide d’expressions d’objet et à l’aide des types de classe.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="d8b4f-117">Dans les deux cas, l’expression de type ou un objet de classe fournit des corps de méthode pour les méthodes abstraites de l’interface.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="d8b4f-118">Les implémentations sont spécifiques à chaque type qui implémente l’interface.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="d8b4f-119">Par conséquent, les méthodes d’interface sur différents types peuvent différer de l’autre.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="d8b4f-120">Les mots clés `interface` et `end`, qui marquent le début et la fin de la définition, sont facultatifs lorsque vous utilisez la syntaxe simplifiée.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="d8b4f-121">Si vous n’utilisez pas ces mots clés, le compilateur tente de déduire si le type est une classe ou une interface en analysant les constructions que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="d8b4f-122">Si vous définissez un membre ou utilisez la syntaxe de la classe, le type est interprété comme une classe.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="d8b4f-123">Style de codage .NET consiste à commencer à toutes les interfaces avec un investissement `I`.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>


## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="d8b4f-124">Implémentation des Interfaces à l’aide de Types de classe</span><span class="sxs-lookup"><span data-stu-id="d8b4f-124">Implementing Interfaces by Using Class Types</span></span>
<span data-ttu-id="d8b4f-125">Vous pouvez implémenter une ou plusieurs interfaces dans un type de classe à l’aide de la `interface` (mot clé), le nom de l’interface et le `with` (mot clé), suivi par les définitions de membre d’interface, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="d8b4f-126">Implémentations d’interface sont héritées, toutes les classes dérivées n’avez pas besoin d’implémenter de nouveau les.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>


## <a name="calling-interface-methods"></a><span data-ttu-id="d8b4f-127">Appel de méthodes d’Interface</span><span class="sxs-lookup"><span data-stu-id="d8b4f-127">Calling Interface Methods</span></span>
<span data-ttu-id="d8b4f-128">Méthodes d’interface peuvent être appelées uniquement par le biais de l’interface, et non par le biais de n’importe quel objet du type qui implémente l’interface.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="d8b4f-129">Par conséquent, vous devrez peut-être un upcast vers le type d’interface à l’aide de la `:>` opérateur ou la `upcast` opérateur afin d’appeler ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="d8b4f-130">Pour appeler la méthode d’interface lorsque vous avez un objet de type `SomeClass`, vous devez effectuer un upcast l’objet pour le type d’interface, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="d8b4f-131">Une alternative consiste à déclarer une méthode sur l’objet qui effectue un upcast et appelle la méthode d’interface, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="d8b4f-132">Implémentation des Interfaces à l’aide d’Expressions d’objet</span><span class="sxs-lookup"><span data-stu-id="d8b4f-132">Implementing Interfaces by Using Object Expressions</span></span>
<span data-ttu-id="d8b4f-133">Expressions d’objet constituent une méthode rapide pour implémenter une interface.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="d8b4f-134">Ils sont utiles lorsque vous n’êtes pas obligé de créer un type nommé, et vous souhaitez qu’un objet qui prend en charge les méthodes d’interface, sans méthodes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="d8b4f-135">Une expression d’objet est illustrée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a><span data-ttu-id="d8b4f-136">Héritage de l'interface</span><span class="sxs-lookup"><span data-stu-id="d8b4f-136">Interface Inheritance</span></span>
<span data-ttu-id="d8b4f-137">Interfaces peuvent hériter d’une ou plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="d8b4f-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a><span data-ttu-id="d8b4f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8b4f-138">See Also</span></span>
[<span data-ttu-id="d8b4f-139">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="d8b4f-139">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="d8b4f-140">Expressions d'objet</span><span class="sxs-lookup"><span data-stu-id="d8b4f-140">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="d8b4f-141">Classes</span><span class="sxs-lookup"><span data-stu-id="d8b4f-141">Classes</span></span>](classes.md)
