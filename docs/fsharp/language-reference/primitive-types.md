---
title: Types primitifs (F#)
description: "Découvrez les types primitifs fondamentaux utilisés dans le langage F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a><span data-ttu-id="d60ca-104">Types primitifs</span><span class="sxs-lookup"><span data-stu-id="d60ca-104">Primitive Types</span></span>

<span data-ttu-id="d60ca-105">Cette rubrique répertorie les types primitifs fondamentaux utilisés dans le langage F #.</span><span class="sxs-lookup"><span data-stu-id="d60ca-105">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="d60ca-106">Elle fournit également les types .NET correspondants et les valeurs minimales et maximales pour chaque type.</span><span class="sxs-lookup"><span data-stu-id="d60ca-106">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="d60ca-107">Résumé des Types primitifs</span><span class="sxs-lookup"><span data-stu-id="d60ca-107">Summary of Primitive Types</span></span>
<span data-ttu-id="d60ca-108">Le tableau suivant résume les propriétés des types F # primitifs.</span><span class="sxs-lookup"><span data-stu-id="d60ca-108">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="d60ca-109">Type</span><span class="sxs-lookup"><span data-stu-id="d60ca-109">Type</span></span>|<span data-ttu-id="d60ca-110">Type .NET</span><span class="sxs-lookup"><span data-stu-id="d60ca-110">.NET type</span></span>|<span data-ttu-id="d60ca-111">Description</span><span class="sxs-lookup"><span data-stu-id="d60ca-111">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="d60ca-112">Les valeurs possibles sont `true` et `false`.</span><span class="sxs-lookup"><span data-stu-id="d60ca-112">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="d60ca-113">Valeurs comprises entre 0 et 255.</span><span class="sxs-lookup"><span data-stu-id="d60ca-113">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="d60ca-114">Valeurs entre -128 et 127.</span><span class="sxs-lookup"><span data-stu-id="d60ca-114">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="d60ca-115">Valeurs comprises entre-32 768 et 32 767.</span><span class="sxs-lookup"><span data-stu-id="d60ca-115">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="d60ca-116">Valeurs comprises entre 0 et 65535.</span><span class="sxs-lookup"><span data-stu-id="d60ca-116">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="d60ca-117">Valeurs d’allant de -2,147,483,648 à 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="d60ca-117">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="d60ca-118">Valeurs de 0 à 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="d60ca-118">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="d60ca-119">Valeurs de -9,223,372,036,854,775,808 à 9,223,372,036,854,775,807.</span><span class="sxs-lookup"><span data-stu-id="d60ca-119">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="d60ca-120">Valeurs comprises entre 0 et 18,446,744,073,709,551,615.</span><span class="sxs-lookup"><span data-stu-id="d60ca-120">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="d60ca-121">Un pointeur natif comme un entier signé.</span><span class="sxs-lookup"><span data-stu-id="d60ca-121">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="d60ca-122">Un pointeur natif en tant qu’entier non signé.</span><span class="sxs-lookup"><span data-stu-id="d60ca-122">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="d60ca-123">Valeurs de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="d60ca-123">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="d60ca-124">Texte Unicode.</span><span class="sxs-lookup"><span data-stu-id="d60ca-124">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="d60ca-125">Type de données qui comporte au moins 28 chiffres significatifs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="d60ca-125">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="d60ca-126">non applicable</span><span class="sxs-lookup"><span data-stu-id="d60ca-126">not applicable</span></span>|<span data-ttu-id="d60ca-127">Indique l’absence d’une valeur réelle.</span><span class="sxs-lookup"><span data-stu-id="d60ca-127">Indicates the absence of an actual value.</span></span> <span data-ttu-id="d60ca-128">Le type n'a qu’une seule valeur formelle, ce qui est indiquée `()`.</span><span class="sxs-lookup"><span data-stu-id="d60ca-128">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="d60ca-129">La valeur de l’unité, `()`, est souvent utilisé comme espace réservé où une valeur est requise, mais aucune valeur réelle n’est disponible ou de sens.</span><span class="sxs-lookup"><span data-stu-id="d60ca-129">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="d60ca-130">Indique le type ou la valeur.</span><span class="sxs-lookup"><span data-stu-id="d60ca-130">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="d60ca-131">Un type à virgule flottante 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d60ca-131">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="d60ca-132">Un type à virgule flottante 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d60ca-132">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="d60ca-133">Vous pouvez effectuer des calculs avec des entiers trop grands pour le type d’entier 64 bits à l’aide de la [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span><span class="sxs-lookup"><span data-stu-id="d60ca-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="d60ca-134">`bigint`n’est pas considéré comme un type primitif ; Il est l’abréviation de `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="d60ca-134">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d60ca-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d60ca-135">See Also</span></span>
[<span data-ttu-id="d60ca-136">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="d60ca-136">F# Language Reference</span></span>](index.md)
