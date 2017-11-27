---
title: "Énumérations (F#)"
description: "Découvrez comment utiliser les énumérations F # à la place de littéraux pour rendre votre code plus lisible et plus facile à gérer."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9272bf5a-9a9f-4314-9e34-a3248e5244f5
ms.openlocfilehash: de0273900b707c99e6fb1bcc84e5c2b9ef2bc725
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="enumerations"></a><span data-ttu-id="a0951-104">Énumérations</span><span class="sxs-lookup"><span data-stu-id="a0951-104">Enumerations</span></span>

<span data-ttu-id="a0951-105">*Énumérations*, également appelé *enums*, sont des types intégraux où les étiquettes sont assignés à un sous-ensemble de valeurs.</span><span class="sxs-lookup"><span data-stu-id="a0951-105">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="a0951-106">Vous pouvez les utiliser à la place de littéraux pour rendre le code plus lisible et plus facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="a0951-106">You can use them in place of literals to make code more readable and maintainable.</span></span>


## <a name="syntax"></a><span data-ttu-id="a0951-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0951-107">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="a0951-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="a0951-108">Remarks</span></span>
<span data-ttu-id="a0951-109">Une énumération ressemble beaucoup à une union discriminée qui possède des valeurs simples, à ceci près que les valeurs peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="a0951-109">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="a0951-110">Les valeurs sont généralement des entiers qui commencent à 0 ou 1, ou des entiers qui représentent les positions de bit.</span><span class="sxs-lookup"><span data-stu-id="a0951-110">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="a0951-111">Si une énumération est destinée à représenter des positions de bits, vous devez également utiliser le [indicateurs](xref:System.FlagsAttribute) attribut.</span><span class="sxs-lookup"><span data-stu-id="a0951-111">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="a0951-112">Le type sous-jacent de l’énumération est déterminé à partir du littéral est utilisé, afin que, par exemple, vous pouvez utiliser des littéraux avec un suffixe, comme `1u`, `2u`, et ainsi de suite, pour un entier non signé (`uint32`) type.</span><span class="sxs-lookup"><span data-stu-id="a0951-112">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="a0951-113">Lorsque vous faites référence aux valeurs nommées, vous devez utiliser le nom du type d’énumération en tant que qualificateur, autrement dit, `enum-name.value1`, pas seulement `value1`.</span><span class="sxs-lookup"><span data-stu-id="a0951-113">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="a0951-114">Ce comportement diffère de celui des unions discriminées.</span><span class="sxs-lookup"><span data-stu-id="a0951-114">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="a0951-115">Il s’agit, car les énumérations ont toujours la [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribut.</span><span class="sxs-lookup"><span data-stu-id="a0951-115">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="a0951-116">Le code suivant illustre la déclaration et l’utilisation d’une énumération.</span><span class="sxs-lookup"><span data-stu-id="a0951-116">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="a0951-117">Vous pouvez facilement convertir des énumérations au type sous-jacent à l’aide de l’opérateur approprié, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="a0951-117">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="a0951-118">Les types énumérés peuvent avoir un des types sous-jacents suivants : `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, et `char`.</span><span class="sxs-lookup"><span data-stu-id="a0951-118">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="a0951-119">Les types énumération sont représentés dans le .NET Framework comme des types qui sont héritées de `System.Enum`, qui à son tour est hérité de `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="a0951-119">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="a0951-120">Par conséquent, ils sont des types de valeur qui sont trouvent sur la pile ou inline dans l’objet conteneur, et toute valeur du type sous-jacent est une valeur valide de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="a0951-120">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="a0951-121">Ceci est important lorsque les critères spéciaux sur l’énumération des valeurs, car vous devez fournir un modèle qui intercepte les valeurs sans nom.</span><span class="sxs-lookup"><span data-stu-id="a0951-121">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="a0951-122">Le `enum` fonction dans la bibliothèque F # peut être utilisée pour générer une valeur d’énumération, même une valeur autre que prédéfinis, de valeurs nommées.</span><span class="sxs-lookup"><span data-stu-id="a0951-122">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="a0951-123">Vous utilisez la `enum` fonctionnent comme suit.</span><span class="sxs-lookup"><span data-stu-id="a0951-123">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="a0951-124">La valeur par défaut `enum` fonctionne avec le type `int32`.</span><span class="sxs-lookup"><span data-stu-id="a0951-124">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="a0951-125">Par conséquent, il ne peut pas être utilisé avec les types d’énumération qui ont d’autres types sous-jacents.</span><span class="sxs-lookup"><span data-stu-id="a0951-125">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="a0951-126">Au lieu de cela, utilisez ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="a0951-126">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a><span data-ttu-id="a0951-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0951-127">See Also</span></span>
[<span data-ttu-id="a0951-128">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="a0951-128">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="a0951-129">Casts et conversions</span><span class="sxs-lookup"><span data-stu-id="a0951-129">Casting and Conversions</span></span>](casting-and-conversions.md)
