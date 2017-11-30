---
title: "Integer, type de données (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69c7fb6caf5d9a10c7d033d1ba0a05c9230d472c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="dbd15-102">Type de données Integer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbd15-102">Integer data type (Visual Basic)</span></span>
<span data-ttu-id="dbd15-103">Contient des entiers 32 bits (4 octets) signés dont la valeur est comprise entre -2 147 483 648 et 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="dbd15-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbd15-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="dbd15-104">Remarks</span></span>
 <span data-ttu-id="dbd15-105">Le type de données `Integer` offre des performances optimales sur un processeur 32 bits.</span><span class="sxs-lookup"><span data-stu-id="dbd15-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="dbd15-106">Les autres types intégraux sont plus lents à charger et à stocker en provenance et à destination de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="dbd15-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="dbd15-107">La valeur par défaut de `Integer` est 0.</span><span class="sxs-lookup"><span data-stu-id="dbd15-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="dbd15-108">Attributions de littéral</span><span class="sxs-lookup"><span data-stu-id="dbd15-108">Literal assignments</span></span>

<span data-ttu-id="dbd15-109">Vous pouvez déclarer et initialiser une `Integer` variable en lui assignant un décimal littéral, un littéral hexadécimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="dbd15-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="dbd15-110">Si le littéral entier est en dehors de la plage de `Integer` (autrement dit, s’il est inférieur à <xref:System.Int32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int32.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="dbd15-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="dbd15-111">Dans l’exemple suivant, les entiers égaux à 16 342 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `Integer`.</span><span class="sxs-lookup"><span data-stu-id="dbd15-111">In the following example, integers equal to 16,342 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="dbd15-112">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="dbd15-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="dbd15-113">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="dbd15-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="dbd15-114">À partir de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur de chiffres pour améliorer la lisibilité, comme l’exemple suivant montre le.</span><span class="sxs-lookup"><span data-stu-id="dbd15-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="dbd15-115">Littéraux numériques peuvent également inclure le `I` [caractère de type](../../programming-guide\language-features\data-types/type-characters.md) pour désigner le `Integer` type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dbd15-115">Numeric literals can also include the `I` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H035826I
```

## <a name="programming-tips"></a><span data-ttu-id="dbd15-116">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="dbd15-116">Programming tips</span></span>

-   <span data-ttu-id="dbd15-117">**Considérations sur l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="dbd15-117">**Interop Considerations.**</span></span> <span data-ttu-id="dbd15-118">Si vous utilisez des composants non écrits pour le .NET Framework, tels que des objets Automation ou COM, n’oubliez pas que `Integer` a une largeur de données différente (16 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="dbd15-118">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="dbd15-119">Si vous passez un argument de 16 bits à un tel composant, déclarez-le en tant que type de données `Short` et non `Integer` dans votre nouveau code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dbd15-119">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="dbd15-120">**Étendues.**</span><span class="sxs-lookup"><span data-stu-id="dbd15-120">**Widening.**</span></span> <span data-ttu-id="dbd15-121">Le type de données `Integer` s'étend à `Long`, `Decimal`, `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="dbd15-121">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="dbd15-122">Cela signifie que vous pouvez convertir `Integer` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbd15-122">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="dbd15-123">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="dbd15-123">**Type Characters.**</span></span> <span data-ttu-id="dbd15-124">L'ajout du caractère de type littéral `I` à un littéral force ce dernier en type de données `Integer`.</span><span class="sxs-lookup"><span data-stu-id="dbd15-124">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="dbd15-125">L'ajout du caractère de type identificateur `%` à un identificateur force ce dernier en type `Integer`.</span><span class="sxs-lookup"><span data-stu-id="dbd15-125">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
-   <span data-ttu-id="dbd15-126">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="dbd15-126">**Framework Type.**</span></span> <span data-ttu-id="dbd15-127">Le type correspondant dans le .NET Framework est la structure <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbd15-127">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="dbd15-128">Plage</span><span class="sxs-lookup"><span data-stu-id="dbd15-128">Range</span></span>

<span data-ttu-id="dbd15-129">Si vous essayez d'assigner à une variable de type intégral un nombre situé hors de la plage de ce type, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="dbd15-129">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="dbd15-130">Si vous essayez de lui assigner une fraction, le nombre est arrondi à la valeur entière supérieure ou inférieure la plus proche.</span><span class="sxs-lookup"><span data-stu-id="dbd15-130">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="dbd15-131">Si le nombre est proche à l'identique de deux valeurs entières, la valeur est arrondie à l'entier pair le plus proche.</span><span class="sxs-lookup"><span data-stu-id="dbd15-131">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="dbd15-132">Ce comportement réduit les erreurs d'arrondi qui résultent de l'arrondissement cohérent d'une valeur du milieu dans un seul sens.</span><span class="sxs-lookup"><span data-stu-id="dbd15-132">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="dbd15-133">Le code suivant présente des exemples d'arrondi.</span><span class="sxs-lookup"><span data-stu-id="dbd15-133">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="dbd15-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbd15-134">See also</span></span>

<span data-ttu-id="dbd15-135"><xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="dbd15-135"><xref:System.Int32?displayProperty=nameWithType></span></span>   
 [<span data-ttu-id="dbd15-136">Types de données</span><span class="sxs-lookup"><span data-stu-id="dbd15-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="dbd15-137">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="dbd15-137">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="dbd15-138">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="dbd15-138">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="dbd15-139">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="dbd15-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="dbd15-140">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="dbd15-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="dbd15-141">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="dbd15-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
