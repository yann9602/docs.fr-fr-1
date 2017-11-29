---
title: "Short, type de données (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
f1_keywords: vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: fef948debed69cf9fb7b0e6bb65eb0ddbe497a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="6fa7e-102">Type de données short (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fa7e-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="6fa7e-103">Contient des entiers 16 bits (2 octets) de valeurs comprises entre-32 768 à 32 767 signés.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fa7e-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="6fa7e-104">Remarks</span></span>  
 <span data-ttu-id="6fa7e-105">Utilisez le `Short` type de données pour contenir des valeurs entières qui ne nécessitent pas la largeur totale des données de `Integer`.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="6fa7e-106">Dans certains cas, le common language runtime peut pack votre `Short` variables étroitement ensemble et d’enregistrer la consommation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="6fa7e-107">La valeur par défaut de `Short` est 0.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="6fa7e-108">Attributions de littéral</span><span class="sxs-lookup"><span data-stu-id="6fa7e-108">Literal assignments</span></span>

<span data-ttu-id="6fa7e-109">Vous pouvez déclarer et initialiser une `Short` variable en lui assignant un décimal littéral, un littéral hexadécimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="6fa7e-110">Si le littéral entier est en dehors de la plage de `Short` (autrement dit, s’il est inférieur à <xref:System.Int16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="6fa7e-111">Dans l’exemple suivant, les entiers égal à 1,034 sont représentées sous forme de nombre décimal, hexadécimal, et les littéraux binaires sont converties implicitement à partir [entier](integer-data-type.md) à `Short` valeurs.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="6fa7e-112">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="6fa7e-113">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="6fa7e-114">À partir de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur de chiffres pour améliorer la lisibilité, comme l’exemple suivant montre le.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="6fa7e-115">Littéraux numériques peuvent également inclure le `S` [caractère de type](../../programming-guide\language-features\data-types/type-characters.md) pour désigner le `Short` type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-115">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H0326S
```

## <a name="programming-tips"></a><span data-ttu-id="6fa7e-116">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="6fa7e-116">Programming tips</span></span>

-   <span data-ttu-id="6fa7e-117">**Étendues.**</span><span class="sxs-lookup"><span data-stu-id="6fa7e-117">**Widening.**</span></span> <span data-ttu-id="6fa7e-118">Le `Short` type de données s’étend à `Integer`, `Long`, `Decimal`, `Single`, ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-118">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="6fa7e-119">Cela signifie que vous pouvez convertir `Short` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-119">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="6fa7e-120">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="6fa7e-120">**Type Characters.**</span></span> <span data-ttu-id="6fa7e-121">L'ajout du caractère de type littéral `S` à un littéral force ce dernier en type de données `Short`.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-121">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="6fa7e-122">`Short`n’a aucun caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-122">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="6fa7e-123">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="6fa7e-123">**Framework Type.**</span></span> <span data-ttu-id="6fa7e-124">Le type correspondant dans le .NET Framework est la structure <xref:System.Int16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6fa7e-124">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa7e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fa7e-125">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="6fa7e-126">Types de données</span><span class="sxs-lookup"><span data-stu-id="6fa7e-126">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="6fa7e-127">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="6fa7e-127">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="6fa7e-128">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="6fa7e-128">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="6fa7e-129">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="6fa7e-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="6fa7e-130">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="6fa7e-130">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="6fa7e-131">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="6fa7e-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
