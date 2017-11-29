---
title: "Long, type de données (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e21ed43ddc6efb018df0581faed1ebf270ab3ca
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="ae7af-102">Type de données long (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae7af-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="ae7af-103">Contient des entiers (8 octets) de 64 bits dont la valeur de -9,223,372,036,854,775,808 à 9,223,372,036,854,775,807 signés (9.2... E + 18).</span><span class="sxs-lookup"><span data-stu-id="ae7af-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae7af-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="ae7af-104">Remarks</span></span>

 <span data-ttu-id="ae7af-105">Utilisez le `Long` type de données pour contenir des nombres entiers qui sont trop volumineuses pour tenir la `Integer` type de données.</span><span class="sxs-lookup"><span data-stu-id="ae7af-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>  
  
 <span data-ttu-id="ae7af-106">La valeur par défaut de `Long` est 0.</span><span class="sxs-lookup"><span data-stu-id="ae7af-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="ae7af-107">Attributions de littéral</span><span class="sxs-lookup"><span data-stu-id="ae7af-107">Literal assignments</span></span> 

<span data-ttu-id="ae7af-108">Vous pouvez déclarer et initialiser une `Long` variable en lui assignant un décimal littéral, un littéral hexadécimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="ae7af-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ae7af-109">Si le littéral entier est en dehors de la plage de `Long` (autrement dit, s’il est inférieur à <xref:System.Int64.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int64.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="ae7af-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ae7af-110">Dans l’exemple suivant, les entiers égaux à 4 294 967 296 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `Long`.</span><span class="sxs-lookup"><span data-stu-id="ae7af-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> <span data-ttu-id="ae7af-111">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="ae7af-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ae7af-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="ae7af-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ae7af-113">À partir de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur de chiffres pour améliorer la lisibilité, comme l’exemple suivant montre le.</span><span class="sxs-lookup"><span data-stu-id="ae7af-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="ae7af-114">Littéraux numériques peuvent également inclure le `L` [caractère de type](../../programming-guide\language-features\data-types/type-characters.md) pour désigner le `Long` type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ae7af-114">Numeric literals can also include the `L` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H0FAC0326L
```

## <a name="programming-tips"></a><span data-ttu-id="ae7af-115">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="ae7af-115">Programming tips</span></span>

-   <span data-ttu-id="ae7af-116">**Considérations sur l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="ae7af-116">**Interop Considerations.**</span></span> <span data-ttu-id="ae7af-117">Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que `Long` a une largeur de données différente (32 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="ae7af-117">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="ae7af-118">Si vous passez un argument de 32 bits à un tel composant, déclarez-le en tant que `Integer` au lieu de `Long` dans votre nouveau code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae7af-118">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="ae7af-119">**Étendues.**</span><span class="sxs-lookup"><span data-stu-id="ae7af-119">**Widening.**</span></span> <span data-ttu-id="ae7af-120">Le `Long` type de données s’étend à `Decimal`, `Single`, ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="ae7af-120">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="ae7af-121">Cela signifie que vous pouvez convertir `Long` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae7af-121">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="ae7af-122">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="ae7af-122">**Type Characters.**</span></span> <span data-ttu-id="ae7af-123">L'ajout du caractère de type littéral `L` à un littéral force ce dernier en type de données `Long`.</span><span class="sxs-lookup"><span data-stu-id="ae7af-123">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="ae7af-124">L'ajout du caractère de type identificateur `&` à un identificateur force ce dernier en type `Long`.</span><span class="sxs-lookup"><span data-stu-id="ae7af-124">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>  
  
-   <span data-ttu-id="ae7af-125">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="ae7af-125">**Framework Type.**</span></span> <span data-ttu-id="ae7af-126">Le type correspondant dans le .NET Framework est la structure <xref:System.Int64?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae7af-126">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>  

## <a name="see-also"></a><span data-ttu-id="ae7af-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae7af-127">See also</span></span>

<span data-ttu-id="ae7af-128"><xref:System.Int64>[Des Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="ae7af-128"><xref:System.Int64> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="ae7af-129">[Type de données Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="ae7af-129">[Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="ae7af-130">[Type de données de type short](../../../visual-basic/language-reference/data-types/short-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="ae7af-130">[Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md) </span></span>  
<span data-ttu-id="ae7af-131">[Fonctions de Conversion de type](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="ae7af-131">[Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="ae7af-132">[Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="ae7af-132">[Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
[<span data-ttu-id="ae7af-133">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="ae7af-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
