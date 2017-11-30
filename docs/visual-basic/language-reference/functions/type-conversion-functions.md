---
title: "Fonctions de conversion de types de données (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 117cd4ce038a533715bbc86558545f0f223dd149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="125c1-102">Fonctions de conversion de types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="125c1-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="125c1-103">Ces fonctions sont compilées en ligne, ce qui signifie que le code de conversion fait partie du code qui évalue l’expression.</span><span class="sxs-lookup"><span data-stu-id="125c1-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="125c1-104">Parfois, il n’existe aucun appel à une procédure pour effectuer la conversion, ce qui améliore les performances.</span><span class="sxs-lookup"><span data-stu-id="125c1-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="125c1-105">Chaque fonction convertit une expression en un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="125c1-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="125c1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="125c1-106">Syntax</span></span>  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## <a name="part"></a><span data-ttu-id="125c1-107">Élément</span><span class="sxs-lookup"><span data-stu-id="125c1-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="125c1-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="125c1-108">Required.</span></span> <span data-ttu-id="125c1-109">Toute expression de type de données source.</span><span class="sxs-lookup"><span data-stu-id="125c1-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="125c1-110">Type de données de valeur de retour</span><span class="sxs-lookup"><span data-stu-id="125c1-110">Return Value Data Type</span></span>  
 <span data-ttu-id="125c1-111">Le nom de la fonction détermine le type de données de la valeur de que retour, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="125c1-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="125c1-112">Nom de la fonction</span><span class="sxs-lookup"><span data-stu-id="125c1-112">Function name</span></span>|<span data-ttu-id="125c1-113">Type de données de retour</span><span class="sxs-lookup"><span data-stu-id="125c1-113">Return data type</span></span>|<span data-ttu-id="125c1-114">Plage de `expression` argument</span><span class="sxs-lookup"><span data-stu-id="125c1-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="125c1-115">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="125c1-116">Valide `Char` ou `String` ou expression numérique.</span><span class="sxs-lookup"><span data-stu-id="125c1-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="125c1-117">Byte (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="125c1-118">0 à 255 (non signé) ; parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="125c1-118">0 through 255 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CChar`|[<span data-ttu-id="125c1-119">Char (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-119">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="125c1-120">Valide `Char` ou `String` expression ; seul premier caractère d’un `String` est converti ; valeur peut être 0 et 65 535 (non signé).</span><span class="sxs-lookup"><span data-stu-id="125c1-120">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="125c1-121">Date (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-121">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="125c1-122">Toute représentation valide d’une date et une heure.</span><span class="sxs-lookup"><span data-stu-id="125c1-122">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="125c1-123">Double (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-123">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="125c1-124">-1, 79769313486231570E + 308 à - 4, 94065645841246544E-324 pour les valeurs négatives ; 4, 94065645841246544E-324 à 1, 79769313486231570E + 308 pour les valeurs positives.</span><span class="sxs-lookup"><span data-stu-id="125c1-124">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="125c1-125">Decimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-125">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="125c1-126">+/-79,228,162,514,264,337,593,543,950,335 pour les nombres à échelle zéro, les nombres sans décimales.</span><span class="sxs-lookup"><span data-stu-id="125c1-126">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="125c1-127">Pour les nombres à 28 décimales, la plage est +/-7,9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="125c1-127">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="125c1-128">Le plus petit nombre possible de zéro est 0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="125c1-128">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="125c1-129">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="125c1-130">2,147,483,648 et 2 147 483 647 ; parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="125c1-130">-2,147,483,648 through 2,147,483,647; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CLng`|[<span data-ttu-id="125c1-131">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-131">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="125c1-132">-9,223,372,036,854,775,808 à 9,223,372,036,854,775,807 ; parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="125c1-132">-9,223,372,036,854,775,808 through 9,223,372,036,854,775,807; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CObj`|[<span data-ttu-id="125c1-133">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-133">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="125c1-134">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="125c1-134">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="125c1-135">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-135">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="125c1-136">-128 à 127 ; parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="125c1-136">-128 through 127; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CShort`|[<span data-ttu-id="125c1-137">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-137">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="125c1-138">-32 768 à 32 767 ; parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="125c1-138">-32,768 through 32,767; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CSng`|[<span data-ttu-id="125c1-139">Single (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-139">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="125c1-140">-3, 402823E + 38 à - 1, 401298E-45 pour les valeurs négatives ; 1, 401298E-45 à 3, 402823E + 38 pour les valeurs positives.</span><span class="sxs-lookup"><span data-stu-id="125c1-140">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="125c1-141">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-141">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="125c1-142">Retourne pour `CStr` dépendent de la `expression` argument.</span><span class="sxs-lookup"><span data-stu-id="125c1-142">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="125c1-143">Consultez [retournent des valeurs pour la fonction CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="125c1-143">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="125c1-144">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-144">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="125c1-145">0 à 4 294 967 295 (non signé) ; parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="125c1-145">0 through 4,294,967,295 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CULng`|[<span data-ttu-id="125c1-146">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-146">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="125c1-147">0 et 18,446,744,073,709,551,615 (non signé) ; parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="125c1-147">0 through 18,446,744,073,709,551,615 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CUShort`|[<span data-ttu-id="125c1-148">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="125c1-148">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="125c1-149">0 à 65 535 (non signé) ; parties fractionnaires sont arrondies. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="125c1-149">0 through 65,535 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
  
 <span data-ttu-id="125c1-150"><sup>1</sup> fractionnaire peut être soumis à un type spécial de l’arrondi appelée *l’arrondi bancaire*.</span><span class="sxs-lookup"><span data-stu-id="125c1-150"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="125c1-151">Pour plus d’informations, consultez la section « Notes ».</span><span class="sxs-lookup"><span data-stu-id="125c1-151">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="125c1-152">Remarques</span><span class="sxs-lookup"><span data-stu-id="125c1-152">Remarks</span></span>  
 <span data-ttu-id="125c1-153">En règle générale, vous devez utiliser les fonctions de conversion de type Visual Basic, plutôt que les méthodes .NET Framework, tel que `ToString()`, soit sur le <xref:System.Convert> classe ou sur une structure de type classe.</span><span class="sxs-lookup"><span data-stu-id="125c1-153">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="125c1-154">Les fonctions Visual Basic sont conçues pour une interaction optimale avec code Visual Basic, et elles s’avèrent également votre code source plus courte et plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="125c1-154">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="125c1-155">En outre, les méthodes de conversion .NET Framework ne produisent pas toujours les mêmes résultats que les fonctions Visual Basic, par exemple lors de la conversion `Boolean` à `Integer`.</span><span class="sxs-lookup"><span data-stu-id="125c1-155">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="125c1-156">Pour plus d’informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="125c1-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="125c1-157">Comportement</span><span class="sxs-lookup"><span data-stu-id="125c1-157">Behavior</span></span>  
  
-   <span data-ttu-id="125c1-158">**Contrainte.**</span><span class="sxs-lookup"><span data-stu-id="125c1-158">**Coercion.**</span></span> <span data-ttu-id="125c1-159">En règle générale, vous pouvez utiliser les fonctions de conversion de type de données pour forcer le résultat d’une opération sur un type de données particulier plutôt que le type de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="125c1-159">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="125c1-160">Par exemple, utilisez `CDec` pour forcer l’opération arithmétique décimale dans les cas où simple précision, double précision ou arithmétique sur les entiers a généralement lieu.</span><span class="sxs-lookup"><span data-stu-id="125c1-160">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   <span data-ttu-id="125c1-161">**Échec des Conversions.**</span><span class="sxs-lookup"><span data-stu-id="125c1-161">**Failed Conversions.**</span></span> <span data-ttu-id="125c1-162">Si le `expression` passé à la fonction est en dehors de la plage du type de données vers lequel il doit être converti, un <xref:System.OverflowException> se produit.</span><span class="sxs-lookup"><span data-stu-id="125c1-162">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   <span data-ttu-id="125c1-163">**Parties fractionnaires.**</span><span class="sxs-lookup"><span data-stu-id="125c1-163">**Fractional Parts.**</span></span> <span data-ttu-id="125c1-164">Lorsque vous convertissez une valeur non entière à un entier de type, les fonctions de conversion d’entier (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, et `CUShort`) supprimer le fractions de seconde partie et arrondissent la valeur à l’entier le plus proche.</span><span class="sxs-lookup"><span data-stu-id="125c1-164">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="125c1-165">Si la partie fractionnaire est exactement 0,5, les fonctions de conversion d’entier arrondissent à l’entier pair le plus proche de.</span><span class="sxs-lookup"><span data-stu-id="125c1-165">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="125c1-166">Par exemple, 0,5 est arrondi à 0 et 1,5 et 2,5 que sont arrondis à 2.</span><span class="sxs-lookup"><span data-stu-id="125c1-166">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="125c1-167">Il est parfois appelé *l’arrondi bancaire*, et son objectif est de compenser un écart qui pourrait s’accumuler lors de l’ajout de plusieurs nombres ensemble.</span><span class="sxs-lookup"><span data-stu-id="125c1-167">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="125c1-168">`CInt`et `CLng` diffèrent le <xref:Microsoft.VisualBasic.Conversion.Int%2A> et <xref:Microsoft.VisualBasic.Conversion.Fix%2A> les fonctions tronquent, au lieu d’arrondissent, la partie fractionnaire d’un nombre.</span><span class="sxs-lookup"><span data-stu-id="125c1-168">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="125c1-169">En outre, `Fix` et `Int` retournent toujours une valeur du même type de données que vous passez.</span><span class="sxs-lookup"><span data-stu-id="125c1-169">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   <span data-ttu-id="125c1-170">**Conversions de date et d’heure.**</span><span class="sxs-lookup"><span data-stu-id="125c1-170">**Date/Time Conversions.**</span></span> <span data-ttu-id="125c1-171">Utilisez le <xref:Microsoft.VisualBasic.Information.IsDate%2A> afin de déterminer si une valeur peut être convertie en une date et une heure.</span><span class="sxs-lookup"><span data-stu-id="125c1-171">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="125c1-172">`CDate`reconnaît les littéraux de date et heure mais pas de valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="125c1-172">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="125c1-173">Pour convertir un Visual Basic 6.0 `Date` valeur un `Date` valeur en Visual Basic 2005 ou version ultérieure, vous pouvez utiliser la <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="125c1-173">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="125c1-174">**Indépendant des valeurs de Date/heure.**</span><span class="sxs-lookup"><span data-stu-id="125c1-174">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="125c1-175">Le [Type de données Date](../../../visual-basic/language-reference/data-types/date-data-type.md) contient toujours des informations de date et heure.</span><span class="sxs-lookup"><span data-stu-id="125c1-175">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="125c1-176">À des fins de conversion de type, Visual Basic considère le 1/1/0001 (le 1er janvier de l’année 1) soit un *valeur neutre* pour la date et 00:00:00 (minuit) comme une valeur neutre pour l’heure.</span><span class="sxs-lookup"><span data-stu-id="125c1-176">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="125c1-177">Si vous convertissez un `Date` valeur à une chaîne, `CStr` n’inclut pas de valeurs neutres dans la chaîne résultante.</span><span class="sxs-lookup"><span data-stu-id="125c1-177">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="125c1-178">Par exemple, si vous convertissez `#January 1, 0001 9:30:00#` en une chaîne, le résultat est « 9:30:00 AM » ; les informations de date sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="125c1-178">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="125c1-179">Toutefois, les informations de date sont toujours présentes dans la version d’origine `Date` valeur et peuvent être récupérées avec des fonctions telles que <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> (fonction).</span><span class="sxs-lookup"><span data-stu-id="125c1-179">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   <span data-ttu-id="125c1-180">**Respect de la culture.**</span><span class="sxs-lookup"><span data-stu-id="125c1-180">**Culture Sensitivity.**</span></span> <span data-ttu-id="125c1-181">Les fonctions de conversion de type impliquant des chaînes effectuent des conversions selon les paramètres de culture actuels de l’application.</span><span class="sxs-lookup"><span data-stu-id="125c1-181">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="125c1-182">Par exemple, `CDate` reconnaît les formats de date selon les paramètres régionaux de votre système.</span><span class="sxs-lookup"><span data-stu-id="125c1-182">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="125c1-183">Vous devez fournir le jour, le mois et l’année dans l’ordre correct pour vos paramètres régionaux, ou la date ne peut pas être interprétée correctement.</span><span class="sxs-lookup"><span data-stu-id="125c1-183">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="125c1-184">Un format de date long n’est pas reconnu s’il contient une chaîne day of week, tels que « Mercredi ».</span><span class="sxs-lookup"><span data-stu-id="125c1-184">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="125c1-185">Si vous devez convertir vers ou depuis une représentation sous forme de chaîne d’une valeur dans un format différent de celui spécifié par les paramètres régionaux, vous ne pouvez pas utiliser les fonctions de conversion de type Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="125c1-185">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="125c1-186">Pour ce faire, utilisez le `ToString(IFormatProvider)` et `Parse(String, IFormatProvider)` méthodes de type de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="125c1-186">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="125c1-187">Par exemple, utilisez <xref:System.Double.Parse%2A?displayProperty=nameWithType> lors de la conversion d’une chaîne à un `Double`et utiliser <xref:System.Double.ToString%2A?displayProperty=nameWithType> lors de la conversion d’une valeur de type `Double` en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="125c1-187">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="125c1-188">CType Function</span><span class="sxs-lookup"><span data-stu-id="125c1-188">CType Function</span></span>  
 <span data-ttu-id="125c1-189">Le [CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md) accepte un deuxième argument, `typename`et force `expression` à `typename`, où `typename` peut être n’importe quel type de données, une structure, une classe ou une interface à laquelle il existe une conversion valide.</span><span class="sxs-lookup"><span data-stu-id="125c1-189">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="125c1-190">Pour obtenir une comparaison de `CType` avec les autres mots-clés de conversion de type, consultez [opérateur DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) et [opérateur TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="125c1-190">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="125c1-191">CBool, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-191">CBool Example</span></span>  
 <span data-ttu-id="125c1-192">L’exemple suivant utilise le `CBool` fonction pour convertir les expressions à `Boolean` valeurs.</span><span class="sxs-lookup"><span data-stu-id="125c1-192">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="125c1-193">Si une expression prend une valeur différente de zéro, `CBool` retourne `True`; sinon, elle retourne `False`.</span><span class="sxs-lookup"><span data-stu-id="125c1-193">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="125c1-194">CByte, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-194">CByte Example</span></span>  
 <span data-ttu-id="125c1-195">L’exemple suivant utilise le `CByte` fonction pour convertir une expression à un `Byte`.</span><span class="sxs-lookup"><span data-stu-id="125c1-195">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a><span data-ttu-id="125c1-196">CChar, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-196">CChar Example</span></span>  
 <span data-ttu-id="125c1-197">L’exemple suivant utilise le `CChar` fonction pour convertir le premier caractère d’un `String` expression à un `Char` type.</span><span class="sxs-lookup"><span data-stu-id="125c1-197">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 <span data-ttu-id="125c1-198">L’argument d’entrée `CChar` doit être de type de données `Char` ou `String`.</span><span class="sxs-lookup"><span data-stu-id="125c1-198">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="125c1-199">Vous ne pouvez pas utiliser `CChar` pour convertir un nombre en un caractère, car `CChar` ne peut pas accepter un type de données numérique.</span><span class="sxs-lookup"><span data-stu-id="125c1-199">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="125c1-200">L’exemple suivant obtient un nombre représentant un point de code (code de caractère) et le convertit en caractère correspondant.</span><span class="sxs-lookup"><span data-stu-id="125c1-200">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="125c1-201">Elle utilise le <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> fonction pour obtenir la chaîne de chiffres, `CInt` pour convertir la chaîne en type `Integer`, et `ChrW` pour convertir le nombre en type `Char`.</span><span class="sxs-lookup"><span data-stu-id="125c1-201">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a><span data-ttu-id="125c1-202">CDate, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-202">CDate Example</span></span>  
 <span data-ttu-id="125c1-203">L’exemple suivant utilise le `CDate` fonction pour convertir des chaînes à `Date` valeurs.</span><span class="sxs-lookup"><span data-stu-id="125c1-203">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="125c1-204">En règle générale, le codage en dur les dates et heures sous forme de chaînes (comme indiqué dans cet exemple) n’est pas recommandé.</span><span class="sxs-lookup"><span data-stu-id="125c1-204">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="125c1-205">Utiliser des littéraux de date et heure, tels que #Feb 12, &#1969; et # 4:45:23 PM #, à la place.</span><span class="sxs-lookup"><span data-stu-id="125c1-205">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="125c1-206">CDbl, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-206">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a><span data-ttu-id="125c1-207">CDec, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-207">CDec Example</span></span>  
 <span data-ttu-id="125c1-208">L’exemple suivant utilise le `CDec` fonction pour convertir une valeur numérique en `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="125c1-208">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a><span data-ttu-id="125c1-209">Exemple de CInt</span><span class="sxs-lookup"><span data-stu-id="125c1-209">CInt Example</span></span>  
 <span data-ttu-id="125c1-210">L’exemple suivant utilise le `CInt` fonction pour convertir une valeur en `Integer`.</span><span class="sxs-lookup"><span data-stu-id="125c1-210">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a><span data-ttu-id="125c1-211">CLng, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-211">CLng Example</span></span>  
 <span data-ttu-id="125c1-212">L’exemple suivant utilise le `CLng` fonction pour convertir des valeurs à `Long`.</span><span class="sxs-lookup"><span data-stu-id="125c1-212">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a><span data-ttu-id="125c1-213">CObj, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-213">CObj Example</span></span>  
 <span data-ttu-id="125c1-214">L’exemple suivant utilise le `CObj` fonction pour convertir une valeur numérique en `Object`.</span><span class="sxs-lookup"><span data-stu-id="125c1-214">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="125c1-215">Le `Object` variable contient uniquement un pointeur de quatre octets, qui pointe vers le `Double` valeur assignée.</span><span class="sxs-lookup"><span data-stu-id="125c1-215">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="125c1-216">Exemple CSByte</span><span class="sxs-lookup"><span data-stu-id="125c1-216">CSByte Example</span></span>  
 <span data-ttu-id="125c1-217">L’exemple suivant utilise le `CSByte` fonction pour convertir une valeur numérique en `SByte`.</span><span class="sxs-lookup"><span data-stu-id="125c1-217">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a><span data-ttu-id="125c1-218">CShort, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-218">CShort Example</span></span>  
 <span data-ttu-id="125c1-219">L’exemple suivant utilise le `CShort` fonction pour convertir une valeur numérique en `Short`.</span><span class="sxs-lookup"><span data-stu-id="125c1-219">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a><span data-ttu-id="125c1-220">CSng, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-220">CSng Example</span></span>  
 <span data-ttu-id="125c1-221">L’exemple suivant utilise le `CSng` fonction pour convertir des valeurs à `Single`.</span><span class="sxs-lookup"><span data-stu-id="125c1-221">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a><span data-ttu-id="125c1-222">Exemple de la fonction CStr</span><span class="sxs-lookup"><span data-stu-id="125c1-222">CStr Example</span></span>  
 <span data-ttu-id="125c1-223">L’exemple suivant utilise le `CStr` fonction pour convertir une valeur numérique en `String`.</span><span class="sxs-lookup"><span data-stu-id="125c1-223">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 <span data-ttu-id="125c1-224">L’exemple suivant utilise le `CStr` fonction pour convertir `Date` valeurs `String` valeurs.</span><span class="sxs-lookup"><span data-stu-id="125c1-224">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 <span data-ttu-id="125c1-225">`CStr`restitue toujours un `Date` valeur dans le format de date courte pour les paramètres régionaux, par exemple, « 15/6/2003 4:35:47 PM ».</span><span class="sxs-lookup"><span data-stu-id="125c1-225">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="125c1-226">Toutefois, `CStr` supprime le *valeurs neutres* de 1/1/0001 pour la date et 00:00:00 pour l’heure.</span><span class="sxs-lookup"><span data-stu-id="125c1-226">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="125c1-227">Pour plus d’informations sur les valeurs retournées par `CStr`, consultez [les valeurs de retour pour la fonction CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="125c1-227">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="125c1-228">Exemple CUInt</span><span class="sxs-lookup"><span data-stu-id="125c1-228">CUInt Example</span></span>  
 <span data-ttu-id="125c1-229">L’exemple suivant utilise le `CUInt` fonction pour convertir une valeur numérique en `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="125c1-229">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a><span data-ttu-id="125c1-230">CULng, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-230">CULng Example</span></span>  
 <span data-ttu-id="125c1-231">L’exemple suivant utilise le `CULng` fonction pour convertir une valeur numérique en `ULong`.</span><span class="sxs-lookup"><span data-stu-id="125c1-231">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a><span data-ttu-id="125c1-232">CUShort, exemple</span><span class="sxs-lookup"><span data-stu-id="125c1-232">CUShort Example</span></span>  
 <span data-ttu-id="125c1-233">L’exemple suivant utilise le `CUShort` fonction pour convertir une valeur numérique en `UShort`.</span><span class="sxs-lookup"><span data-stu-id="125c1-233">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="125c1-234">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="125c1-234">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 <xref:Microsoft.VisualBasic.Strings.Format%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="125c1-235">Fonctions de conversion</span><span class="sxs-lookup"><span data-stu-id="125c1-235">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="125c1-236">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="125c1-236">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
