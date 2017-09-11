---
title: "uint (référence C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 18
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
ms.openlocfilehash: 4342c08ab536f45a2e3b5fa6fe94839436600a4a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="uint-c-reference"></a><span data-ttu-id="9fbf3-102">uint (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9fbf3-102">uint (C# Reference)</span></span>

<span data-ttu-id="9fbf3-103">Le mot clé `uint` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="9fbf3-104">Type</span><span class="sxs-lookup"><span data-stu-id="9fbf3-104">Type</span></span>|<span data-ttu-id="9fbf3-105">Plage</span><span class="sxs-lookup"><span data-stu-id="9fbf3-105">Range</span></span>|<span data-ttu-id="9fbf3-106">Taille</span><span class="sxs-lookup"><span data-stu-id="9fbf3-106">Size</span></span>|<span data-ttu-id="9fbf3-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9fbf3-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`uint`|<span data-ttu-id="9fbf3-108">de 0 à 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="9fbf3-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="9fbf3-109">Entier 32 bits non signé</span><span class="sxs-lookup"><span data-stu-id="9fbf3-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=fullName>|  
  
 <span data-ttu-id="9fbf3-110">**Note** Le type `uint` n’est pas conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="9fbf3-111">Utilisez `int` autant que possible.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-111">Use `int` whenever possible.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="9fbf3-112">Littéraux</span><span class="sxs-lookup"><span data-stu-id="9fbf3-112">Literals</span></span>  

<span data-ttu-id="9fbf3-113">Vous pouvez déclarer et initialiser une variable `uint` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="9fbf3-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="9fbf3-114">Si le littéral entier est en dehors de la plage de `uint` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=fullName> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=fullName>), une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=fullName> or greater than <xref:System.UInt32.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span>

<span data-ttu-id="9fbf3-115">Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `uint`.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>  
  
<span data-ttu-id="9fbf3-116">[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]</span><span class="sxs-lookup"><span data-stu-id="9fbf3-116">[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="9fbf3-117">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-117">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="9fbf3-118">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-118">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="9fbf3-119">À compter de C# 7, vous pouvez également utiliser le caractère de soulignement, `_`, comme séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-119">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="9fbf3-120">[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]</span><span class="sxs-lookup"><span data-stu-id="9fbf3-120">[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]</span></span>  
 
 <span data-ttu-id="9fbf3-121">Les littéraux entiers peuvent également inclure un suffixe qui désigne le type.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="9fbf3-122">Le suffixe `U` ou « u » désigne un type `uint` ou `ulong`, selon la valeur numérique du littéral.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-122">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="9fbf3-123">L’exemple suivant utilise le suffixe `u` pour désigner un entier non signé des deux types.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-123">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="9fbf3-124">Notez que le premier littéral est un type `uint`, car sa valeur est inférieure à <xref:System.UInt32.MaxValue?displayProperty=fullName>, tandis que le deuxième est un type `ulong`, car sa valeur est supérieure à <xref:System.UInt32.MaxValue?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-124">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=fullName>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=fullName>.</span></span>

<span data-ttu-id="9fbf3-125">[!code-cs[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="9fbf3-125">[!code-cs[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]</span></span>  
 
<span data-ttu-id="9fbf3-126">Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée :</span><span class="sxs-lookup"><span data-stu-id="9fbf3-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="9fbf3-127">int</span><span class="sxs-lookup"><span data-stu-id="9fbf3-127">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="9fbf3-128">long</span><span class="sxs-lookup"><span data-stu-id="9fbf3-128">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="9fbf3-129">ulong</span><span class="sxs-lookup"><span data-stu-id="9fbf3-129">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a><span data-ttu-id="9fbf3-130">Conversions</span><span class="sxs-lookup"><span data-stu-id="9fbf3-130">Conversions</span></span>  
 <span data-ttu-id="9fbf3-131">Il existe une conversion implicite prédéfinie de `uint` en [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) et [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="9fbf3-131">There is a predefined implicit conversion from `uint` to [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="9fbf3-132">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9fbf3-132">For example:</span></span>  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 <span data-ttu-id="9fbf3-133">Il existe une conversion implicite prédéfinie de [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `uint`.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-133">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `uint`.</span></span> <span data-ttu-id="9fbf3-134">Dans le cas contraire, vous devez utiliser un cast.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-134">Otherwise you must use a cast.</span></span> <span data-ttu-id="9fbf3-135">Par exemple, l’instruction d’assignation suivante génère une erreur de compilation sans cast :</span><span class="sxs-lookup"><span data-stu-id="9fbf3-135">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 <span data-ttu-id="9fbf3-136">Remarquez également qu’il n’existe pas de conversion implicite des types virgule flottante en `uint`.</span><span class="sxs-lookup"><span data-stu-id="9fbf3-136">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="9fbf3-137">Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :</span><span class="sxs-lookup"><span data-stu-id="9fbf3-137">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 <span data-ttu-id="9fbf3-138">Pour plus d’informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="9fbf3-138">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="9fbf3-139">Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="9fbf3-139">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9fbf3-140">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9fbf3-140">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9fbf3-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fbf3-141">See Also</span></span>  
 <span data-ttu-id="9fbf3-142"><xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="9fbf3-142"><xref:System.UInt32></span></span>   
 <span data-ttu-id="9fbf3-143">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9fbf3-143">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9fbf3-144">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9fbf3-144">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9fbf3-145">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9fbf3-145">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="9fbf3-146">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="9fbf3-146">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="9fbf3-147">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="9fbf3-147">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="9fbf3-148">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="9fbf3-148">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="9fbf3-149">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="9fbf3-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

