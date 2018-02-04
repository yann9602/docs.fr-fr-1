---
title: "SByte, type de données (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d391d7eea27ec7696dbb4c28da8916c744712f32
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="5acdd-102">SByte, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5acdd-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="5acdd-103">Contient des entiers 8 bits (1 octet) de valeurs comprises entre -128 et 127 signés.</span><span class="sxs-lookup"><span data-stu-id="5acdd-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5acdd-104">Notes</span><span class="sxs-lookup"><span data-stu-id="5acdd-104">Remarks</span></span>

<span data-ttu-id="5acdd-105">Utilisez le `SByte` type de données pour contenir des valeurs entières qui ne nécessitent pas la largeur totale des données de `Integer` ou même la largeur de la moitié des données de `Short`.</span><span class="sxs-lookup"><span data-stu-id="5acdd-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="5acdd-106">Dans certains cas, le common language runtime peut être en mesure de compresser vos `SByte` variables étroitement ensemble et d’enregistrer la consommation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="5acdd-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="5acdd-107">La valeur par défaut de `SByte` est 0.</span><span class="sxs-lookup"><span data-stu-id="5acdd-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="5acdd-108">Attributions de littéral</span><span class="sxs-lookup"><span data-stu-id="5acdd-108">Literal assignments</span></span>
  
<span data-ttu-id="5acdd-109">Vous pouvez déclarer et initialiser une `SByte` variable en lui assignant un décimal littéral, un littéral hexadécimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="5acdd-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="5acdd-110">Dans l’exemple suivant, les entiers égal à-102 sont représentées sous forme de nombre décimal, hexadécimal, et les littéraux binaires sont affectés à `SByte` valeurs.</span><span class="sxs-lookup"><span data-stu-id="5acdd-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="5acdd-111">Cet exemple nécessite que vous compilez avec le `/removeintchecks` commutateur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="5acdd-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> <span data-ttu-id="5acdd-112">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="5acdd-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="5acdd-113">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="5acdd-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="5acdd-114">À partir de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur de chiffres pour améliorer la lisibilité, comme l’exemple suivant montre le.</span><span class="sxs-lookup"><span data-stu-id="5acdd-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

<span data-ttu-id="5acdd-115">À partir de Visual Basic 15.5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octales.</span><span class="sxs-lookup"><span data-stu-id="5acdd-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="5acdd-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5acdd-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="5acdd-117">Si le littéral entier est en dehors de la plage de `SByte` (autrement dit, s’il est inférieur à <xref:System.SByte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.SByte.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="5acdd-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="5acdd-118">Lorsqu’un littéral entier n’a aucun suffixe, un [entier](integer-data-type.md) est déduit.</span><span class="sxs-lookup"><span data-stu-id="5acdd-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="5acdd-119">Si le littéral entier est en dehors de la plage de la `Integer` type, un [Long](long-data-type.md) est déduit.</span><span class="sxs-lookup"><span data-stu-id="5acdd-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="5acdd-120">Cela signifie que, dans les exemples précédents, les littéraux numériques `0x9A` et `0b10011010` sont interprétées comme des entiers signés 32 bits avec la valeur 156, ce qui dépasse <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5acdd-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5acdd-121">Pour compiler le code à ce qui affecte un entier décimal non à un `SByte`, vous pouvez effectuer l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5acdd-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="5acdd-122">Désactiver les vérifications de limites d’entier en compilant avec le `/removeintchecks` commutateur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="5acdd-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="5acdd-123">Utilisez un [caractère de type](../../programming-guide\language-features\data-types/type-characters.md) pour définir explicitement la valeur littérale que vous souhaitez attribuer à la `SByte`.</span><span class="sxs-lookup"><span data-stu-id="5acdd-123">Use a [type character](../../programming-guide\language-features\data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="5acdd-124">L’exemple suivant assigne un littéral négatif `Short` la valeur en un `SByte`.</span><span class="sxs-lookup"><span data-stu-id="5acdd-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="5acdd-125">Notez que, pour les nombres négatifs, le bit de poids fort du mot de poids fort du littéral numérique doit être défini.</span><span class="sxs-lookup"><span data-stu-id="5acdd-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="5acdd-126">Dans le cas de notre exemple, il est de type bit 15 du littéral `Short` valeur.</span><span class="sxs-lookup"><span data-stu-id="5acdd-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="5acdd-127">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="5acdd-127">Programming tips</span></span>
  
-   <span data-ttu-id="5acdd-128">**Conformité CLS.**</span><span class="sxs-lookup"><span data-stu-id="5acdd-128">**CLS Compliance.**</span></span> <span data-ttu-id="5acdd-129">Le `SByte` type de données n’est pas dans le cadre de la [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), un code conforme CLS ne peut pas consommer un composant qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="5acdd-129">The `SByte` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

-   <span data-ttu-id="5acdd-130">**Étendues.**</span><span class="sxs-lookup"><span data-stu-id="5acdd-130">**Widening.**</span></span> <span data-ttu-id="5acdd-131">Le `SByte` type de données s’étend à `Short`, `Integer`, `Long`, `Decimal`, `Single`, et `Double`.</span><span class="sxs-lookup"><span data-stu-id="5acdd-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="5acdd-132">Cela signifie que vous pouvez convertir `SByte` à un de ces types sans rencontrer un <xref:System.OverflowException?displayProperty=nameWithType> erreur.</span><span class="sxs-lookup"><span data-stu-id="5acdd-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="5acdd-133">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="5acdd-133">**Type Characters.**</span></span> <span data-ttu-id="5acdd-134">`SByte`n’a aucun caractère de type littéral ou un caractère de type identificateur.</span><span class="sxs-lookup"><span data-stu-id="5acdd-134">`SByte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="5acdd-135">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="5acdd-135">**Framework Type.**</span></span> <span data-ttu-id="5acdd-136">Le type correspondant dans le .NET Framework est la structure <xref:System.SByte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5acdd-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5acdd-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5acdd-137">See also</span></span>

 <xref:System.SByte?displayProperty=nameWithType>  
 [<span data-ttu-id="5acdd-138">Types de données</span><span class="sxs-lookup"><span data-stu-id="5acdd-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="5acdd-139">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="5acdd-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="5acdd-140">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="5acdd-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="5acdd-141">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="5acdd-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="5acdd-142">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="5acdd-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="5acdd-143">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="5acdd-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="5acdd-144">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="5acdd-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
