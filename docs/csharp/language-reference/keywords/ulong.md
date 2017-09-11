---
title: "ulong (référence C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
dev_langs:
- CSharp
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
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
ms.openlocfilehash: c2da253e4da7a5d6cfa71116e4fcba7816441e92
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ulong-c-reference"></a><span data-ttu-id="1511e-102">ulong (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1511e-102">ulong (C# Reference)</span></span>

<span data-ttu-id="1511e-103">Le mot clé `ulong` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="1511e-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="1511e-104">Type</span><span class="sxs-lookup"><span data-stu-id="1511e-104">Type</span></span>|<span data-ttu-id="1511e-105">Plage</span><span class="sxs-lookup"><span data-stu-id="1511e-105">Range</span></span>|<span data-ttu-id="1511e-106">Taille</span><span class="sxs-lookup"><span data-stu-id="1511e-106">Size</span></span>|<span data-ttu-id="1511e-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1511e-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ulong`|<span data-ttu-id="1511e-108">de 0 à 18 446 744 073 709 551 615</span><span class="sxs-lookup"><span data-stu-id="1511e-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="1511e-109">Entier 64 bits non signé</span><span class="sxs-lookup"><span data-stu-id="1511e-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="1511e-110">Littéraux</span><span class="sxs-lookup"><span data-stu-id="1511e-110">Literals</span></span>  

<span data-ttu-id="1511e-111">Vous pouvez déclarer et initialiser une variable `ulong` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="1511e-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="1511e-112">Si le littéral entier est en dehors de la plage de `ulong` (autrement dit, s’il est inférieur à <xref:System.UInt64.MinValue?displayProperty=fullName> ou supérieur à <xref:System.UInt64.MaxValue?displayProperty=fullName>), une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="1511e-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=fullName> or greater than <xref:System.UInt64.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span> 

<span data-ttu-id="1511e-113">Dans l’exemple suivant, les entiers égaux à 7 934 076 125 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `ulong`.</span><span class="sxs-lookup"><span data-stu-id="1511e-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>  
  
<span data-ttu-id="1511e-114">[!code-cs[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]</span><span class="sxs-lookup"><span data-stu-id="1511e-114">[!code-cs[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="1511e-115">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="1511e-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="1511e-116">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="1511e-116">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="1511e-117">À compter de C# 7, vous pouvez également utiliser le caractère de soulignement, `_`, comme séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1511e-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="1511e-118">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span><span class="sxs-lookup"><span data-stu-id="1511e-118">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span></span>  
 
 <span data-ttu-id="1511e-119">Les littéraux entiers peuvent également inclure un suffixe qui désigne le type.</span><span class="sxs-lookup"><span data-stu-id="1511e-119">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="1511e-120">Le suffixe `UL` ou `ul` identifie sans ambiguïté un littéral numérique comme une valeur `ulong`.</span><span class="sxs-lookup"><span data-stu-id="1511e-120">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="1511e-121">Le suffixe `L` désigne un type `ulong` si la valeur du littéral dépasse <xref:System.Int64.MaxValue?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="1511e-121">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=fullName>.</span></span> <span data-ttu-id="1511e-122">Le suffixe `U` ou `u` désigne un type `ulong` si la valeur du littéral dépasse <xref:System.UInt32.MaxValue?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="1511e-122">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=fullName>.</span></span> <span data-ttu-id="1511e-123">L’exemple suivant utilise le suffixe `ul` pour désigner un entier long :</span><span class="sxs-lookup"><span data-stu-id="1511e-123">The following example uses the `ul` suffix to denote a long integer:</span></span>
 
<span data-ttu-id="1511e-124">[!code-cs[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="1511e-124">[!code-cs[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]</span></span>

<span data-ttu-id="1511e-125">Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée :</span><span class="sxs-lookup"><span data-stu-id="1511e-125">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="1511e-126">int</span><span class="sxs-lookup"><span data-stu-id="1511e-126">int</span></span>](int.md)
2. [<span data-ttu-id="1511e-127">uint</span><span class="sxs-lookup"><span data-stu-id="1511e-127">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="1511e-128">long</span><span class="sxs-lookup"><span data-stu-id="1511e-128">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="1511e-129">Résolution de surcharge du compilateur</span><span class="sxs-lookup"><span data-stu-id="1511e-129">Compiler overload resolution</span></span>
  
 <span data-ttu-id="1511e-130">Une utilisation courante du suffixe est d’appeler des méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="1511e-130">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="1511e-131">Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `ulong` et [int](../../../csharp/language-reference/keywords/int.md) :</span><span class="sxs-lookup"><span data-stu-id="1511e-131">Consider, for example, the following overloaded methods that use `ulong` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 <span data-ttu-id="1511e-132">L’utilisation d’un suffixe avec le paramètre `ulong` garantit que le type correct est appelé, par exemple :</span><span class="sxs-lookup"><span data-stu-id="1511e-132">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="1511e-133">Conversions</span><span class="sxs-lookup"><span data-stu-id="1511e-133">Conversions</span></span>  
 <span data-ttu-id="1511e-134">Il existe une conversion implicite prédéfinie de `ulong` en [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="1511e-134">There is a predefined implicit conversion from `ulong` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="1511e-135">Il n’existe aucune conversion implicite de `ulong` en un type intégral.</span><span class="sxs-lookup"><span data-stu-id="1511e-135">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="1511e-136">Par exemple, l’instruction suivante génère une erreur de compilation sans cast explicite :</span><span class="sxs-lookup"><span data-stu-id="1511e-136">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 <span data-ttu-id="1511e-137">Il existe une conversion implicite prédéfinie de [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `ulong`.</span><span class="sxs-lookup"><span data-stu-id="1511e-137">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `ulong`.</span></span>  
  
 <span data-ttu-id="1511e-138">De plus, il n’existe pas de conversion implicite des types virgule flottante en `ulong`.</span><span class="sxs-lookup"><span data-stu-id="1511e-138">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="1511e-139">Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :</span><span class="sxs-lookup"><span data-stu-id="1511e-139">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 <span data-ttu-id="1511e-140">Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="1511e-140">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="1511e-141">Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="1511e-141">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1511e-142">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1511e-142">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1511e-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1511e-143">See Also</span></span>  
 <span data-ttu-id="1511e-144"><xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="1511e-144"><xref:System.UInt64></span></span>   
 <span data-ttu-id="1511e-145">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1511e-145">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1511e-146">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1511e-146">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1511e-147">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1511e-147">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1511e-148">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="1511e-148">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="1511e-149">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="1511e-149">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="1511e-150">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="1511e-150">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="1511e-151">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="1511e-151">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

