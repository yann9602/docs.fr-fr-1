---
title: "uint (référence C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords: uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d32f7146d1f9e13d8cf0f275f4fd78b693b09d31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="uint-c-reference"></a><span data-ttu-id="9b0be-102">uint (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9b0be-102">uint (C# Reference)</span></span>

<span data-ttu-id="9b0be-103">Le mot clé `uint` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="9b0be-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="9b0be-104">Type</span><span class="sxs-lookup"><span data-stu-id="9b0be-104">Type</span></span>|<span data-ttu-id="9b0be-105">Plage</span><span class="sxs-lookup"><span data-stu-id="9b0be-105">Range</span></span>|<span data-ttu-id="9b0be-106">Taille</span><span class="sxs-lookup"><span data-stu-id="9b0be-106">Size</span></span>|<span data-ttu-id="9b0be-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9b0be-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`uint`|<span data-ttu-id="9b0be-108">de 0 à 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="9b0be-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="9b0be-109">Entier 32 bits non signé</span><span class="sxs-lookup"><span data-stu-id="9b0be-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 <span data-ttu-id="9b0be-110">**Note** Le type `uint` n’est pas conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="9b0be-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="9b0be-111">Utilisez `int` autant que possible.</span><span class="sxs-lookup"><span data-stu-id="9b0be-111">Use `int` whenever possible.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="9b0be-112">Littéraux</span><span class="sxs-lookup"><span data-stu-id="9b0be-112">Literals</span></span>  

<span data-ttu-id="9b0be-113">Vous pouvez déclarer et initialiser une variable `uint` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="9b0be-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="9b0be-114">Si le littéral entier est en dehors de la plage autorisée pour le type `uint` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="9b0be-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="9b0be-115">Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `uint`.</span><span class="sxs-lookup"><span data-stu-id="9b0be-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> <span data-ttu-id="9b0be-116">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="9b0be-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="9b0be-117">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="9b0be-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="9b0be-118">À partir de C# 7, quelques fonctionnalités ont été ajoutées améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="9b0be-118">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="9b0be-119">C# 7.0 permet l’utilisation d’un caractère de soulignement `_`, comme un séparateur de chiffre.</span><span class="sxs-lookup"><span data-stu-id="9b0be-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="9b0be-120">7.2 c# permet `_` à utiliser comme séparateur de chiffres pour un littéral binaire ou en hexadécimal, après le préfixe.</span><span class="sxs-lookup"><span data-stu-id="9b0be-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="9b0be-121">Un littéral décimal n’est pas autorisé à avoir un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="9b0be-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="9b0be-122">Certains exemples sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9b0be-122">Some examples are shown below.</span></span>

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 <span data-ttu-id="9b0be-123">Les littéraux entiers peuvent également inclure un suffixe qui désigne le type.</span><span class="sxs-lookup"><span data-stu-id="9b0be-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="9b0be-124">Le suffixe `U` ou « u » désigne un type `uint` ou `ulong`, selon la valeur numérique du littéral.</span><span class="sxs-lookup"><span data-stu-id="9b0be-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="9b0be-125">L’exemple suivant utilise le suffixe `u` pour désigner un entier non signé des deux types.</span><span class="sxs-lookup"><span data-stu-id="9b0be-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="9b0be-126">Notez que le premier littéral est un type `uint`, car sa valeur est inférieure à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, tandis que le deuxième est un type `ulong`, car sa valeur est supérieure à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b0be-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
<span data-ttu-id="9b0be-127">Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée :</span><span class="sxs-lookup"><span data-stu-id="9b0be-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="9b0be-128">int</span><span class="sxs-lookup"><span data-stu-id="9b0be-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="9b0be-129">long</span><span class="sxs-lookup"><span data-stu-id="9b0be-129">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="9b0be-130">ulong</span><span class="sxs-lookup"><span data-stu-id="9b0be-130">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a><span data-ttu-id="9b0be-131">Conversions</span><span class="sxs-lookup"><span data-stu-id="9b0be-131">Conversions</span></span>  
 <span data-ttu-id="9b0be-132">Il existe une conversion implicite prédéfinie de `uint` en [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) et [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="9b0be-132">There is a predefined implicit conversion from `uint` to [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="9b0be-133">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9b0be-133">For example:</span></span>  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 <span data-ttu-id="9b0be-134">Il existe une conversion implicite prédéfinie de [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `uint`.</span><span class="sxs-lookup"><span data-stu-id="9b0be-134">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `uint`.</span></span> <span data-ttu-id="9b0be-135">Dans le cas contraire, vous devez utiliser un cast.</span><span class="sxs-lookup"><span data-stu-id="9b0be-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="9b0be-136">Par exemple, l’instruction d’assignation suivante génère une erreur de compilation sans cast :</span><span class="sxs-lookup"><span data-stu-id="9b0be-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 <span data-ttu-id="9b0be-137">Remarquez également qu’il n’existe pas de conversion implicite des types virgule flottante en `uint`.</span><span class="sxs-lookup"><span data-stu-id="9b0be-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="9b0be-138">Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :</span><span class="sxs-lookup"><span data-stu-id="9b0be-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 <span data-ttu-id="9b0be-139">Pour plus d’informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="9b0be-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="9b0be-140">Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="9b0be-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9b0be-141">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9b0be-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9b0be-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b0be-142">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="9b0be-143">Référence C#</span><span class="sxs-lookup"><span data-stu-id="9b0be-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9b0be-144">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9b0be-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9b0be-145">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="9b0be-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9b0be-146">Tableau des types intégraux</span><span class="sxs-lookup"><span data-stu-id="9b0be-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="9b0be-147">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="9b0be-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="9b0be-148">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="9b0be-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="9b0be-149">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="9b0be-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
