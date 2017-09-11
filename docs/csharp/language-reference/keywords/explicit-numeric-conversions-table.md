---
title: "Tableau des conversions numériques explicites (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0315810522be319a6bb565c99e1c8f7d1ba4701b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="97317-102">Tableau des conversions numériques explicites (référence C#)</span><span class="sxs-lookup"><span data-stu-id="97317-102">Explicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="97317-103">Une conversion numérique explicite permet de convertir, à l’aide d’une expression de cast, n’importe quel type numérique en un autre type numérique quand il n’existe pas de conversion implicite.</span><span class="sxs-lookup"><span data-stu-id="97317-103">Explicit numeric conversion is used to convert any numeric type to any other numeric type, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="97317-104">Le tableau suivant liste ces conversions.</span><span class="sxs-lookup"><span data-stu-id="97317-104">The following table shows these conversions.</span></span>  
  
 <span data-ttu-id="97317-105">Pour plus d’informations sur les conversions, consultez [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="97317-105">For more information about conversions, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
|<span data-ttu-id="97317-106">De</span><span class="sxs-lookup"><span data-stu-id="97317-106">From</span></span>|<span data-ttu-id="97317-107">À</span><span class="sxs-lookup"><span data-stu-id="97317-107">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="97317-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="97317-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="97317-109">`byte`, `ushort`, `uint`, `ulong` ou `char`</span><span class="sxs-lookup"><span data-stu-id="97317-109">`byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="97317-110">byte</span><span class="sxs-lookup"><span data-stu-id="97317-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="97317-111">`Sbyte` ou `char`</span><span class="sxs-lookup"><span data-stu-id="97317-111">`Sbyte` or `char`</span></span>|  
|[<span data-ttu-id="97317-112">short</span><span class="sxs-lookup"><span data-stu-id="97317-112">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="97317-113">`sbyte`, `byte`, `ushort`, `uint`, `ulong` ou `char`</span><span class="sxs-lookup"><span data-stu-id="97317-113">`sbyte`, `byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="97317-114">ushort</span><span class="sxs-lookup"><span data-stu-id="97317-114">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="97317-115">`sbyte`, `byte`, `short` ou `char`</span><span class="sxs-lookup"><span data-stu-id="97317-115">`sbyte`, `byte`, `short`, or `char`</span></span>|  
|[<span data-ttu-id="97317-116">int</span><span class="sxs-lookup"><span data-stu-id="97317-116">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="97317-117">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong` ou `char`</span><span class="sxs-lookup"><span data-stu-id="97317-117">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`,or `char`</span></span>|  
|[<span data-ttu-id="97317-118">uint</span><span class="sxs-lookup"><span data-stu-id="97317-118">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="97317-119">`sbyte`, `byte`, `short`, `ushort`, `int` ou `char`</span><span class="sxs-lookup"><span data-stu-id="97317-119">`sbyte`, `byte`, `short`, `ushort`, `int`, or `char`</span></span>|  
|[<span data-ttu-id="97317-120">long</span><span class="sxs-lookup"><span data-stu-id="97317-120">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="97317-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong` ou `char`</span><span class="sxs-lookup"><span data-stu-id="97317-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="97317-122">ulong</span><span class="sxs-lookup"><span data-stu-id="97317-122">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="97317-123">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long` ou `char`</span><span class="sxs-lookup"><span data-stu-id="97317-123">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, or `char`</span></span>|  
|[<span data-ttu-id="97317-124">char</span><span class="sxs-lookup"><span data-stu-id="97317-124">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="97317-125">`sbyte`, `byte` ou `short`</span><span class="sxs-lookup"><span data-stu-id="97317-125">`sbyte`, `byte`, or `short`</span></span>|  
|[<span data-ttu-id="97317-126">float</span><span class="sxs-lookup"><span data-stu-id="97317-126">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="97317-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="97317-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`,or `decimal`</span></span>|  
|[<span data-ttu-id="97317-128">double</span><span class="sxs-lookup"><span data-stu-id="97317-128">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="97317-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="97317-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`,or `decimal`</span></span>|  
|[<span data-ttu-id="97317-130">decimal</span><span class="sxs-lookup"><span data-stu-id="97317-130">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="97317-131">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `double`</span><span class="sxs-lookup"><span data-stu-id="97317-131">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, or `double`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97317-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="97317-132">Remarks</span></span>  
  
-   <span data-ttu-id="97317-133">La conversion numérique explicite peut produire un résultat de moindre précision ou entraîner la levée d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="97317-133">The explicit numeric conversion may cause loss of precision or result in throwing exceptions.</span></span>  
  
-   <span data-ttu-id="97317-134">Quand vous convertissez une valeur de type `decimal` en type intégral, la valeur source est arrondie vers zéro à la valeur intégrale la plus proche.</span><span class="sxs-lookup"><span data-stu-id="97317-134">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="97317-135">Si la valeur intégrale obtenue se trouve en dehors de la plage du type de destination, une exception <xref:System.OverflowException> est levée.</span><span class="sxs-lookup"><span data-stu-id="97317-135">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>  
  
-   <span data-ttu-id="97317-136">Quand vous convertissez une valeur `double` ou `float` en type intégral, la valeur est tronquée.</span><span class="sxs-lookup"><span data-stu-id="97317-136">When you convert from a `double` or `float` value to an integral type, the value is truncated.</span></span> <span data-ttu-id="97317-137">Si la valeur intégrale obtenue est en dehors de la plage de la valeur de destination, le résultat dépend du contexte de vérification de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="97317-137">If the resulting integral value is outside the range of the destination value, the result depends on the overflow checking context.</span></span> <span data-ttu-id="97317-138">Dans un contexte vérifié, une exception `OverflowException` est levée, alors que dans un contexte non vérifié, le résultat est une valeur non spécifiée du type de destination.</span><span class="sxs-lookup"><span data-stu-id="97317-138">In a checked context, an `OverflowException` is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>  
  
-   <span data-ttu-id="97317-139">Quand vous convertissez `double` en `float`, la valeur `double` est arrondie à la valeur `float` la plus proche.</span><span class="sxs-lookup"><span data-stu-id="97317-139">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="97317-140">Si la valeur `double` est inférieure ou supérieure à la plage de valeurs autorisées pour le type de destination, la conversion a pour résultat la valeur zéro ou un nombre infini.</span><span class="sxs-lookup"><span data-stu-id="97317-140">If the `double` value is too small or too large to fit into the destination type, the result will be zero or infinity.</span></span>  
  
-   <span data-ttu-id="97317-141">Dans le cas d’une conversion de `float` ou `double` en `decimal`, la valeur source est convertie en une représentation `decimal` et arrondie au nombre le plus proche après la 28ème décimale, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="97317-141">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="97317-142">Selon la valeur de la valeur source, la conversion peut aboutir à l’un des résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="97317-142">Depending on the value of the source value, one of the following results may occur:</span></span>  
  
    -   <span data-ttu-id="97317-143">Si la valeur source est trop petite pour être représentée en tant que `decimal`, le résultat est zéro.</span><span class="sxs-lookup"><span data-stu-id="97317-143">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>  
  
    -   <span data-ttu-id="97317-144">Si la valeur source est une valeur non numérique (NaN), un nombre infini ou une valeur trop grande pour être représentée au format `decimal`, une exception `OverflowException` est levée.</span><span class="sxs-lookup"><span data-stu-id="97317-144">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an `OverflowException` is thrown.</span></span>  
  
-   <span data-ttu-id="97317-145">Quand vous convertissez `decimal` en `float` ou `double`, la valeur `decimal` est arrondie à la valeur `double` ou `float` la plus proche.</span><span class="sxs-lookup"><span data-stu-id="97317-145">When you convert `decimal` to `float` or `double`, the `decimal` value is rounded to the nearest `double` or `float` value.</span></span>  
  
 <span data-ttu-id="97317-146">Pour plus d’informations sur la conversion explicite, consultez Conversions explicites dans la spécification du langage C#.</span><span class="sxs-lookup"><span data-stu-id="97317-146">For more information on explicit conversion, see Explicit in the C# Language Specification.</span></span> <span data-ttu-id="97317-147">Pour plus d’informations sur l’accès à la spécification, consultez [Spécification du langage C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="97317-147">For more information on how to access the spec, see [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97317-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97317-148">See Also</span></span>  
 <span data-ttu-id="97317-149">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="97317-149">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="97317-150">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="97317-150">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="97317-151">[Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="97317-151">[Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span></span>  
 <span data-ttu-id="97317-152">[(), opérateur](../../../csharp/language-reference/operators/invocation-operator.md) </span><span class="sxs-lookup"><span data-stu-id="97317-152">[() Operator](../../../csharp/language-reference/operators/invocation-operator.md) </span></span>  
 <span data-ttu-id="97317-153">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="97317-153">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="97317-154">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="97317-154">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 [<span data-ttu-id="97317-155">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="97317-155">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)

