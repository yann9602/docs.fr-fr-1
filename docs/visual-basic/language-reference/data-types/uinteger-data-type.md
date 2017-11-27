---
title: "UInteger, type de données"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f3852bd56d11c19e327e6c2f3e23cfb082a54e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="uinteger-data-type"></a><span data-ttu-id="fcffb-102">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="fcffb-102">UInteger data type</span></span>

<span data-ttu-id="fcffb-103">Contient des entiers 32 bits (4 octets) non signés dont la valeur comprise entre 0 et 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="fcffb-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcffb-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="fcffb-104">Remarks</span></span>

 <span data-ttu-id="fcffb-105">Le `UInteger` type de données fournit la plus grande valeur non signée dans la largeur des données la plus efficace.</span><span class="sxs-lookup"><span data-stu-id="fcffb-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="fcffb-106">La valeur par défaut de `UInteger` est 0.</span><span class="sxs-lookup"><span data-stu-id="fcffb-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="fcffb-107">Attributions de littéral</span><span class="sxs-lookup"><span data-stu-id="fcffb-107">Literal assignments</span></span>

<span data-ttu-id="fcffb-108">Vous pouvez déclarer et initialiser une `UInteger` variable en lui assignant un décimal littéral, un littéral hexadécimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="fcffb-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="fcffb-109">Si le littéral entier est en dehors de la plage de `UInteger` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="fcffb-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="fcffb-110">Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="fcffb-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="fcffb-111">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="fcffb-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="fcffb-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="fcffb-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="fcffb-113">À partir de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur de chiffres pour améliorer la lisibilité, comme l’exemple suivant montre le.</span><span class="sxs-lookup"><span data-stu-id="fcffb-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="fcffb-114">Littéraux numériques peuvent également inclure le `UI` ou `ui` [caractère de type](../../programming-guide\language-features\data-types/type-characters.md) pour désigner le `UInteger` type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fcffb-114">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H0FAC14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="fcffb-115">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="fcffb-115">Programming tips</span></span>

 <span data-ttu-id="fcffb-116">Le `UInteger` et `Integer` des types de données fournissent des performances optimales sur un processeur 32 bits, car les types d’entier plus petits (`UShort`, `Short`, `Byte`, et `SByte`), bien qu’ils utilisent moins de bits, prendre plus de temps charger, stocker et récupérer.</span><span class="sxs-lookup"><span data-stu-id="fcffb-116">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
-   <span data-ttu-id="fcffb-117">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="fcffb-117">**Negative Numbers.**</span></span> <span data-ttu-id="fcffb-118">Étant donné que `UInteger` est un type non signé, il ne peut pas représenter un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="fcffb-118">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="fcffb-119">Si vous utilisez le moins unaire (`-`) opérateur sur une expression qui correspond au type `UInteger`, Visual Basic convertit l’expression à `Long` première.</span><span class="sxs-lookup"><span data-stu-id="fcffb-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
-   <span data-ttu-id="fcffb-120">**Conformité CLS.**</span><span class="sxs-lookup"><span data-stu-id="fcffb-120">**CLS Compliance.**</span></span> <span data-ttu-id="fcffb-121">Le `UInteger` type de données n’est pas dans le cadre de la [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), un code conforme CLS ne peut pas consommer un composant qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="fcffb-121">The `UInteger` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="fcffb-122">**Considérations sur l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="fcffb-122">**Interop Considerations.**</span></span> <span data-ttu-id="fcffb-123">Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, gardez à l’esprit que les types tels que `uint` peut avoir une largeur de données différente (16 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="fcffb-123">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="fcffb-124">Si vous passez un argument de 16 bits à un tel composant, déclarez-le en tant que `UShort` au lieu de `UInteger` dans votre code managé de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fcffb-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
-   <span data-ttu-id="fcffb-125">**Étendues.**</span><span class="sxs-lookup"><span data-stu-id="fcffb-125">**Widening.**</span></span> <span data-ttu-id="fcffb-126">Le `UInteger` type de données s’étend à `Long`, `ULong`, `Decimal`, `Single`, et `Double`.</span><span class="sxs-lookup"><span data-stu-id="fcffb-126">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="fcffb-127">Cela signifie que vous pouvez convertir `UInteger` à un de ces types sans rencontrer un <xref:System.OverflowException?displayProperty=nameWithType> erreur.</span><span class="sxs-lookup"><span data-stu-id="fcffb-127">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="fcffb-128">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="fcffb-128">**Type Characters.**</span></span> <span data-ttu-id="fcffb-129">L’ajout de caractères de type littéral `UI` à un littéral force ce dernier à la `UInteger` type de données.</span><span class="sxs-lookup"><span data-stu-id="fcffb-129">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="fcffb-130">`UInteger`n’a aucun caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="fcffb-130">`UInteger` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="fcffb-131">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="fcffb-131">**Framework Type.**</span></span> <span data-ttu-id="fcffb-132">Le type correspondant dans le .NET Framework est la structure <xref:System.UInt32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcffb-132">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcffb-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcffb-133">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="fcffb-134">Types de données</span><span class="sxs-lookup"><span data-stu-id="fcffb-134">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="fcffb-135">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="fcffb-135">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="fcffb-136">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="fcffb-136">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="fcffb-137">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="fcffb-137">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="fcffb-138">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="fcffb-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
