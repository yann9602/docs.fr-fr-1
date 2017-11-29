---
title: "Délégués (F#)"
description: "Apprenez à utiliser avec les délégués en F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 719948a3-83ba-4618-82d6-a22945c3f4b0
ms.openlocfilehash: c929a342ab4c5098062417691a99cee3b007d2d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="ece78-104">Délégués</span><span class="sxs-lookup"><span data-stu-id="ece78-104">Delegates</span></span>

<span data-ttu-id="ece78-105">Un délégué représente un appel de fonction en tant qu’objet.</span><span class="sxs-lookup"><span data-stu-id="ece78-105">A delegate represents a function call as an object.</span></span> <span data-ttu-id="ece78-106">En F #, vous devez normalement utiliser des valeurs de fonction pour représenter des fonctions comme valeurs de première classe ; Toutefois, les délégués sont utilisés dans le .NET Framework et ils sont nécessaires lorsque vous interagissez avec les API qui attendent les.</span><span class="sxs-lookup"><span data-stu-id="ece78-106">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="ece78-107">Ils peuvent également être utilisés lors de la création de bibliothèques conçues pour utiliser d’autres langages .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ece78-107">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="ece78-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ece78-108">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="ece78-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="ece78-109">Remarks</span></span>
<span data-ttu-id="ece78-110">Dans la syntaxe précédente, `type1` représente le type d’argument ou les types et `type2` représente le type de retour.</span><span class="sxs-lookup"><span data-stu-id="ece78-110">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="ece78-111">Les types d’arguments qui sont représentées par `type1` sont automatiquement curryfiés.</span><span class="sxs-lookup"><span data-stu-id="ece78-111">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="ece78-112">Cela signifie que pour ce type que vous utilisez une forme de tuple si les arguments de la fonction cible sont curryfiés et un tuple entre parenthèses pour les arguments qui sont déjà sous la forme de tuple.</span><span class="sxs-lookup"><span data-stu-id="ece78-112">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="ece78-113">La curryfication automatique supprime un jeu de parenthèses, laissant un argument de tuple qui correspond à la méthode cible.</span><span class="sxs-lookup"><span data-stu-id="ece78-113">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="ece78-114">Reportez-vous à l’exemple de code pour la syntaxe à utiliser dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="ece78-114">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="ece78-115">Les délégués peuvent être attachés à des valeurs de fonction F # et statiques ou méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="ece78-115">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="ece78-116">Les valeurs de fonction F # peuvent être passées directement en tant qu’arguments aux constructeurs délégués.</span><span class="sxs-lookup"><span data-stu-id="ece78-116">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="ece78-117">Pour une méthode statique, vous construisez le délégué en utilisant le nom de la classe et la méthode.</span><span class="sxs-lookup"><span data-stu-id="ece78-117">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="ece78-118">Pour une méthode d’instance, vous fournissez l’instance d’objet et la méthode dans un seul argument.</span><span class="sxs-lookup"><span data-stu-id="ece78-118">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="ece78-119">Dans les deux cas, le membre opérateur d’accès (`.`) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ece78-119">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="ece78-120">Le `Invoke` méthode sur le type délégué appelle la fonction encapsulée.</span><span class="sxs-lookup"><span data-stu-id="ece78-120">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="ece78-121">En outre, les délégués peuvent être passés en tant que valeurs de fonction en référençant le nom de la méthode Invoke sans les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="ece78-121">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="ece78-122">Le code suivant illustre la syntaxe pour créer des délégués qui représentent les différentes méthodes dans une classe.</span><span class="sxs-lookup"><span data-stu-id="ece78-122">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="ece78-123">Selon si la méthode est une méthode statique ou une méthode d’instance, et qu’il possède des arguments sous la forme de tuple ou de la forme curryfiée, la syntaxe de déclaration et l’assignation du délégué est un peu différente.</span><span class="sxs-lookup"><span data-stu-id="ece78-123">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="ece78-124">Le code suivant illustre certaines des différentes méthodes que vous pouvez utiliser des délégués.</span><span class="sxs-lookup"><span data-stu-id="ece78-124">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="ece78-125">La sortie de l’exemple de code précédent est comme suit.</span><span class="sxs-lookup"><span data-stu-id="ece78-125">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="ece78-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ece78-126">See Also</span></span>
[<span data-ttu-id="ece78-127">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="ece78-127">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="ece78-128">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="ece78-128">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="ece78-129">Événements</span><span class="sxs-lookup"><span data-stu-id="ece78-129">Events</span></span>](members/events.md)
