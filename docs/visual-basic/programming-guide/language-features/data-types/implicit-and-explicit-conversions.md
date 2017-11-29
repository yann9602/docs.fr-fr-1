---
title: Conversions implicites et explicites (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e9dd698e1cc84464cd12d33767feec960c511ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="205ed-102">Conversions implicites et explicites (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="205ed-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="205ed-103">Un *conversion implicite* ne requiert pas de syntaxe particulière dans le code source.</span><span class="sxs-lookup"><span data-stu-id="205ed-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="205ed-104">Dans l’exemple suivant, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] convertit implicitement la valeur de `k` à une valeur à virgule flottante simple précision avant de l’assigner à `q`.</span><span class="sxs-lookup"><span data-stu-id="205ed-104">In the following example, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="205ed-105">Un *conversion explicite* utilise une conversion de type mot clé.</span><span class="sxs-lookup"><span data-stu-id="205ed-105">An *explicit conversion* uses a type conversion keyword.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="205ed-106">fournit plusieurs de ces mots clés, qui forcent une expression entre parenthèses pour le type de données souhaité.</span><span class="sxs-lookup"><span data-stu-id="205ed-106"> provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="205ed-107">Ces mots clés agissent comme des fonctions, mais le compilateur génère le code inline, par conséquent, l’exécution est légèrement plus rapidement qu’avec un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="205ed-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="205ed-108">Dans l’extension suivante de l’exemple précédent, le `CInt` (mot clé) convertit la valeur de `q` en un entier avant de l’assigner à `k`.</span><span class="sxs-lookup"><span data-stu-id="205ed-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="205ed-109">Mots clés de conversion</span><span class="sxs-lookup"><span data-stu-id="205ed-109">Conversion Keywords</span></span>  
 <span data-ttu-id="205ed-110">Le tableau suivant montre les mots clés de conversion disponibles.</span><span class="sxs-lookup"><span data-stu-id="205ed-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="205ed-111">Mot clé de conversion de type</span><span class="sxs-lookup"><span data-stu-id="205ed-111">Type conversion keyword</span></span>|<span data-ttu-id="205ed-112">Convertit une expression en type de données</span><span class="sxs-lookup"><span data-stu-id="205ed-112">Converts an expression to data type</span></span>|<span data-ttu-id="205ed-113">Types de données autorisés d’expression à convertir</span><span class="sxs-lookup"><span data-stu-id="205ed-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="205ed-114">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="205ed-115">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="205ed-116">Byte (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="205ed-117">Tout type numérique (y compris `SByte` et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="205ed-118">Char (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="205ed-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="205ed-120">Date (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="205ed-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="205ed-122">Double (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="205ed-123">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="205ed-124">Decimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="205ed-125">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="205ed-126">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="205ed-127">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="205ed-128">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="205ed-129">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="205ed-130">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="205ed-131">Tout type</span><span class="sxs-lookup"><span data-stu-id="205ed-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="205ed-132">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="205ed-133">Tout type numérique (y compris `Byte` et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="205ed-134">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="205ed-135">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="205ed-136">Single (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="205ed-137">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="205ed-138">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="205ed-139">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `Char`, `Char` tableau, `Date`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="205ed-140">Type spécifié après la virgule (`,`)</span><span class="sxs-lookup"><span data-stu-id="205ed-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="205ed-141">Lors de la conversion à un *type de données élémentaire* (y compris un tableau d’un type élémentaire), les mêmes types qu’autorisés pour le mot clé de conversion correspondant</span><span class="sxs-lookup"><span data-stu-id="205ed-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="205ed-142">Lors de la conversion à un *type de données composite*, les interfaces qu’il implémente et les classes dont il hérite</span><span class="sxs-lookup"><span data-stu-id="205ed-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="205ed-143">Lors de la conversion d’une classe ou une structure sur laquelle vous avez surchargé `CType`, cette classe ou structure</span><span class="sxs-lookup"><span data-stu-id="205ed-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="205ed-144">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="205ed-145">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="205ed-146">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="205ed-147">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="205ed-148">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="205ed-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="205ed-149">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="205ed-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="205ed-150">La fonction CType</span><span class="sxs-lookup"><span data-stu-id="205ed-150">The CType Function</span></span>  
 <span data-ttu-id="205ed-151">Le [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) opère sur deux arguments.</span><span class="sxs-lookup"><span data-stu-id="205ed-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="205ed-152">Le premier est l’expression à convertir, et la seconde est la classe de type ou l’objet de données de destination.</span><span class="sxs-lookup"><span data-stu-id="205ed-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="205ed-153">Notez que le premier argument doit être une expression, pas un type.</span><span class="sxs-lookup"><span data-stu-id="205ed-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="205ed-154">`CType`est un *fonction inline*sans générer d’une fonction appelle souvent, ce qui signifie que le code compilé effectue la conversion.</span><span class="sxs-lookup"><span data-stu-id="205ed-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="205ed-155">Cela améliore les performances.</span><span class="sxs-lookup"><span data-stu-id="205ed-155">This improves performance.</span></span>  
  
 <span data-ttu-id="205ed-156">Pour obtenir une comparaison de `CType` avec les autres mots-clés de conversion de type, consultez [opérateur DirectCast](../../../../visual-basic/language-reference/operators/directcast-operator.md) et [opérateur TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="205ed-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="205ed-157">Types élémentaires</span><span class="sxs-lookup"><span data-stu-id="205ed-157">Elementary Types</span></span>  
 <span data-ttu-id="205ed-158">L'exemple suivant montre l'utilisation de `CType`.</span><span class="sxs-lookup"><span data-stu-id="205ed-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="205ed-159">Types composites</span><span class="sxs-lookup"><span data-stu-id="205ed-159">Composite Types</span></span>  
 <span data-ttu-id="205ed-160">Vous pouvez utiliser `CType` pour convertir des valeurs pour les types de données composites ainsi élémentaire.</span><span class="sxs-lookup"><span data-stu-id="205ed-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="205ed-161">Vous pouvez également l’utiliser pour forcer une classe d’objet pour le type de l’un de ses interfaces, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="205ed-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="205ed-162">Types de tableau</span><span class="sxs-lookup"><span data-stu-id="205ed-162">Array Types</span></span>  
 <span data-ttu-id="205ed-163">`CType`peut également convertir des types de données de tableau, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="205ed-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 <span data-ttu-id="205ed-164">Pour plus d’informations et obtenir un exemple, consultez [Conversions de tableau](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="205ed-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="205ed-165">Types définissant CType</span><span class="sxs-lookup"><span data-stu-id="205ed-165">Types Defining CType</span></span>  
 <span data-ttu-id="205ed-166">Vous pouvez définir `CType` sur une classe ou une structure que vous avez définie.</span><span class="sxs-lookup"><span data-stu-id="205ed-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="205ed-167">Cela vous permet de convertir des valeurs vers et depuis le type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="205ed-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="205ed-168">Pour plus d’informations et obtenir un exemple, consultez [Comment : définir un opérateur de Conversion](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="205ed-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="205ed-169">Valeurs utilisées avec un mot clé de conversion doivent être valides pour le type de données de destination, ou une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="205ed-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="205ed-170">Par exemple, si vous tentez de convertir un `Long` à un `Integer`, la valeur de la `Long` doit se trouver dans la plage valide pour le `Integer` type de données.</span><span class="sxs-lookup"><span data-stu-id="205ed-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="205ed-171">Spécification de `CType` à convertir à partir d’un type de classe vers un autre échoue au moment de l’exécution si le type source ne dérive pas du type de destination.</span><span class="sxs-lookup"><span data-stu-id="205ed-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="205ed-172">Un tel échec lève une <xref:System.InvalidCastException> exception.</span><span class="sxs-lookup"><span data-stu-id="205ed-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="205ed-173">Toutefois, si un des types est une structure ou une classe que vous avez défini et si vous avez défini `CType` sur cette structure ou une classe, une conversion peut réussir si elle satisfait aux exigences de votre `CType`.</span><span class="sxs-lookup"><span data-stu-id="205ed-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="205ed-174">Consultez [Comment : définir un opérateur de Conversion](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="205ed-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="205ed-175">Effectuez une conversion explicite est également appelé *cast* une expression à une classe de type ou un objet de données donné.</span><span class="sxs-lookup"><span data-stu-id="205ed-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205ed-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="205ed-176">See Also</span></span>  
 [<span data-ttu-id="205ed-177">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="205ed-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="205ed-178">Conversion entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="205ed-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="205ed-179">Comment : convertir un objet en un autre Type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="205ed-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="205ed-180">Structures</span><span class="sxs-lookup"><span data-stu-id="205ed-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="205ed-181">Types de données</span><span class="sxs-lookup"><span data-stu-id="205ed-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="205ed-182">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="205ed-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="205ed-183">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="205ed-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
