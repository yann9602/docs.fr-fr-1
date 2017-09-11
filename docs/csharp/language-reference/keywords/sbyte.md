---
title: "sbyte (référence C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
dev_langs:
- CSharp
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 17
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
ms.openlocfilehash: 69741a5b9556c769156687584041667312550c17
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="sbyte-c-reference"></a><span data-ttu-id="1314d-102">sbyte (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1314d-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="1314d-103">`sbyte` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="1314d-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="1314d-104">Type</span><span class="sxs-lookup"><span data-stu-id="1314d-104">Type</span></span>|<span data-ttu-id="1314d-105">Plage</span><span class="sxs-lookup"><span data-stu-id="1314d-105">Range</span></span>|<span data-ttu-id="1314d-106">Taille</span><span class="sxs-lookup"><span data-stu-id="1314d-106">Size</span></span>|<span data-ttu-id="1314d-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1314d-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="1314d-108">-128 à 127</span><span class="sxs-lookup"><span data-stu-id="1314d-108">-128 to 127</span></span>|<span data-ttu-id="1314d-109">Entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="1314d-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="1314d-110">Littéraux</span><span class="sxs-lookup"><span data-stu-id="1314d-110">Literals</span></span>  

<span data-ttu-id="1314d-111">Vous pouvez déclarer et initialiser une variable `sbyte` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="1314d-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="1314d-112">Dans l’exemple suivant, les entiers égaux à -102 représentés comme des littéraux décimaux, hexadécimaux et binaires sont convertis à partir de valeurs [int](../../../csharp/language-reference/keywords/int.md) en valeurs `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="1314d-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
<span data-ttu-id="1314d-113">[!code-cs[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]</span><span class="sxs-lookup"><span data-stu-id="1314d-113">[!code-cs[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="1314d-114">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="1314d-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="1314d-115">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="1314d-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="1314d-116">À compter de C# 7, vous pouvez également utiliser le caractère de soulignement, `_`, comme séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1314d-116">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="1314d-117">[!code-cs[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]</span><span class="sxs-lookup"><span data-stu-id="1314d-117">[!code-cs[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]</span></span>  

<span data-ttu-id="1314d-118">Si le littéral entier est en dehors de la plage de `sbyte` (autrement dit, s’il est inférieur à <xref:System.SByte.MinValue?displayProperty=fullName> ou supérieur à <xref:System.SByte.MaxValue?displayProperty=fullName>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="1314d-118">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=fullName> or greater than <xref:System.SByte.MaxValue?displayProperty=fullName>, a compilation error occurs.</span></span> <span data-ttu-id="1314d-119">Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="1314d-119">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="1314d-120">Cela signifie que, dans cet exemple, les littéraux numériques `0x9A` et `0b10011010` sont interprétés comme des entiers signés 32 bits avec une valeur égale à 156, ce qui dépasse <xref:System.SByte.MaxValue?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="1314d-120">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=fullName>.</span></span> <span data-ttu-id="1314d-121">Pour cette raison, l’opérateur de cast est nécessaire et l’attribution doit se produire dans un contexte [non vérifié](unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="1314d-121">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="1314d-122">Résolution de surcharge du compilateur</span><span class="sxs-lookup"><span data-stu-id="1314d-122">Compiler overload resolution</span></span>

 <span data-ttu-id="1314d-123">Un cast doit être utilisé lors de l’appel de méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="1314d-123">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="1314d-124">Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `sbyte` et [int](../../../csharp/language-reference/keywords/int.md) :</span><span class="sxs-lookup"><span data-stu-id="1314d-124">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="1314d-125">L’utilisation du cast `sbyte` garantit l’appel du type correct, par exemple :</span><span class="sxs-lookup"><span data-stu-id="1314d-125">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="1314d-126">Conversions</span><span class="sxs-lookup"><span data-stu-id="1314d-126">Conversions</span></span>  
 <span data-ttu-id="1314d-127">Il existe une conversion implicite prédéfinie de `sbyte` en [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="1314d-127">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="1314d-128">Vous ne pouvez pas convertir implicitement des types numériques non littéraux de taille de stockage supérieure à `sbyte` (voir [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour les tailles de stockage des types intégraux).</span><span class="sxs-lookup"><span data-stu-id="1314d-128">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="1314d-129">Considérons, par exemple, les deux variables `sbyte` `x` et `y` suivantes :</span><span class="sxs-lookup"><span data-stu-id="1314d-129">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="1314d-130">L’instruction d’assignation suivante entraîne une erreur de compilation, car l’expression arithmétique située à droite de l’opérateur d’assignation correspond à [int](../../../csharp/language-reference/keywords/int.md) par défaut.</span><span class="sxs-lookup"><span data-stu-id="1314d-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="1314d-131">Pour corriger ce problème, castez l’expression comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1314d-131">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="1314d-132">Il est cependant possible d’utiliser les instructions suivantes dans lesquelles la variable de destination a une taille de stockage égale ou supérieure :</span><span class="sxs-lookup"><span data-stu-id="1314d-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="1314d-133">Notez aussi qu’il n’existe pas de conversion implicite des types virgule flottante en `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="1314d-133">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="1314d-134">Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :</span><span class="sxs-lookup"><span data-stu-id="1314d-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="1314d-135">Pour plus d’informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="1314d-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="1314d-136">Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="1314d-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1314d-137">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1314d-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1314d-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1314d-138">See Also</span></span>  
 <span data-ttu-id="1314d-139"><xref:System.SByte></span><span class="sxs-lookup"><span data-stu-id="1314d-139"><xref:System.SByte></span></span>   
 <span data-ttu-id="1314d-140">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1314d-140">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1314d-141">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1314d-141">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1314d-142">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1314d-142">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1314d-143">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="1314d-143">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="1314d-144">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="1314d-144">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="1314d-145">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="1314d-145">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="1314d-146">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="1314d-146">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

