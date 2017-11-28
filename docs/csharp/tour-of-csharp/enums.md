---
title: "Énumérations C# - Visite guidée du langage C#"
description: "Découvrir les enums, constantes nommées discrètes en C#"
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 77d315dd87d9cab32605de415674d146eb9115fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="enums"></a><span data-ttu-id="1c4b2-104">Énumérations</span><span class="sxs-lookup"><span data-stu-id="1c4b2-104">Enums</span></span>

<span data-ttu-id="1c4b2-105">Un ***type enum*** est un type valeur distinct avec un ensemble de constantes nommées.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-105">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="1c4b2-106">Vous définissez les enums lorsque vous devez définir un type qui peut avoir un ensemble de valeurs discrètes.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-106">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="1c4b2-107">Ils utilisent un des types entier comme stockage sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-107">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="1c4b2-108">Ils apportent une signification sémantique aux valeurs discrètes.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-108">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="1c4b2-109">L’exemple suivant déclare et utilise un type `enum` nommé `Color` avec trois valeurs de constante, `Red`, `Green` et `Blue`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-109">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="1c4b2-110">Chaque type `enum` a un type intégral appelé ***type sous-jacent*** de type `enum`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-110">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="1c4b2-111">Un type `enum` qui ne déclare pas explicitement un type sous-jacent a un type sous-jacent de `int`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-111">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="1c4b2-112">Le format de stockage d’un type `enum` et la plage de valeurs possibles du type sont déterminés par son type sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-112">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="1c4b2-113">L’ensemble de valeurs qu’un type `enum` peut prendre n’est pas limité par ses membres `enum`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-113">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="1c4b2-114">En particulier, n’importe quelle valeur du type sous-jacent d’une `enum` peut être castée en type `enum`, et une valeur valide distincte de ce type `enum`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-114">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="1c4b2-115">L’exemple suivant déclare un type `enum` nommé `Alignment` avec un type sous-jacent de `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-115">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="1c4b2-116">Comme le montre l’exemple précédent, une déclaration de membre `enum` peut inclure une expression constante qui spécifie la valeur du membre.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-116">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="1c4b2-117">La valeur de constante pour chaque membre `enum` doit être dans la plage du type sous-jacent de l’ `enum`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-117">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="1c4b2-118">Lorsqu’une déclaration de membre `enum` ne spécifie pas explicitement une valeur, le membre reçoit la valeur zéro (s’il est le premier membre dans le type `enum`) ou la valeur du membre `enum` précédent dans le texte plus un.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-118">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="1c4b2-119">Les valeurs `Enum` peuvent être converties en valeurs intégrales et inversement à l’aide des casts de type.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-119">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="1c4b2-120">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1c4b2-120">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="1c4b2-121">La valeur par défaut de n’importe quel type `enum` est la valeur intégrale de zéro convertie en type `enum`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-121">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="1c4b2-122">Dans les cas où les variables sont initialisées automatiquement à une valeur par défaut, il s’agit de la valeur donnée aux variables des types `enum`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-122">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="1c4b2-123">Afin que la valeur par défaut d’un type `enum` soit disponible, le littéral `0` convertit implicitement en n’importe quel type `enum`.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-123">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="1c4b2-124">Ce qui suit est donc autorisé.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-124">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
<span data-ttu-id="1c4b2-125">[Précédent](interfaces.md)
[Suivant](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="1c4b2-125">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
