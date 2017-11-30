---
title: "sbyte (référence C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords: sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 010ac98f523eca5929100f7c51b8b6ef5d11de30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-c-reference"></a><span data-ttu-id="c6b20-102">sbyte (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c6b20-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="c6b20-103">`sbyte` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="c6b20-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="c6b20-104">Type</span><span class="sxs-lookup"><span data-stu-id="c6b20-104">Type</span></span>|<span data-ttu-id="c6b20-105">Plage</span><span class="sxs-lookup"><span data-stu-id="c6b20-105">Range</span></span>|<span data-ttu-id="c6b20-106">Taille</span><span class="sxs-lookup"><span data-stu-id="c6b20-106">Size</span></span>|<span data-ttu-id="c6b20-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c6b20-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="c6b20-108">-128 à 127</span><span class="sxs-lookup"><span data-stu-id="c6b20-108">-128 to 127</span></span>|<span data-ttu-id="c6b20-109">Entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="c6b20-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="c6b20-110">Littéraux</span><span class="sxs-lookup"><span data-stu-id="c6b20-110">Literals</span></span>  

<span data-ttu-id="c6b20-111">Vous pouvez déclarer et initialiser une variable `sbyte` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="c6b20-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="c6b20-112">Dans l’exemple suivant, les entiers égaux à -102 représentés comme des littéraux décimaux, hexadécimaux et binaires sont convertis à partir de valeurs [int](../../../csharp/language-reference/keywords/int.md) en valeurs `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="c6b20-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> <span data-ttu-id="c6b20-113">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="c6b20-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="c6b20-114">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="c6b20-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c6b20-115">À partir de C# 7, quelques fonctionnalités ont été ajoutées améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="c6b20-115">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="c6b20-116">C# 7.0 permet l’utilisation d’un caractère de soulignement `_`, comme un séparateur de chiffre.</span><span class="sxs-lookup"><span data-stu-id="c6b20-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="c6b20-117">7.2 c# permet `_` à utiliser comme séparateur de chiffres pour un littéral binaire ou en hexadécimal, après le préfixe.</span><span class="sxs-lookup"><span data-stu-id="c6b20-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="c6b20-118">Un littéral décimal n’est pas autorisé à avoir un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="c6b20-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

 <span data-ttu-id="c6b20-119">Certains exemples sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c6b20-119">Some examples are shown below.</span></span>

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

<span data-ttu-id="c6b20-120">Si le littéral entier est en dehors de la plage de `sbyte` (autrement dit, s’il est inférieur à <xref:System.SByte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.SByte.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="c6b20-120">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="c6b20-121">Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="c6b20-121">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="c6b20-122">Cela signifie que, dans cet exemple, les littéraux numériques `0x9A` et `0b10011010` sont interprétés comme des entiers signés 32 bits avec une valeur égale à 156, ce qui dépasse <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6b20-122">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c6b20-123">Pour cette raison, l’opérateur de cast est nécessaire et l’attribution doit se produire dans un contexte [non vérifié](unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="c6b20-123">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="c6b20-124">Résolution de surcharge du compilateur</span><span class="sxs-lookup"><span data-stu-id="c6b20-124">Compiler overload resolution</span></span>

 <span data-ttu-id="c6b20-125">Un cast doit être utilisé lors de l’appel de méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="c6b20-125">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="c6b20-126">Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `sbyte` et [int](../../../csharp/language-reference/keywords/int.md) :</span><span class="sxs-lookup"><span data-stu-id="c6b20-126">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="c6b20-127">L’utilisation du cast `sbyte` garantit l’appel du type correct, par exemple :</span><span class="sxs-lookup"><span data-stu-id="c6b20-127">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="c6b20-128">Conversions</span><span class="sxs-lookup"><span data-stu-id="c6b20-128">Conversions</span></span>  
 <span data-ttu-id="c6b20-129">Il existe une conversion implicite prédéfinie de `sbyte` en [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="c6b20-129">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="c6b20-130">Vous ne pouvez pas convertir implicitement des types numériques non littéraux de taille de stockage supérieure à `sbyte` (voir [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour les tailles de stockage des types intégraux).</span><span class="sxs-lookup"><span data-stu-id="c6b20-130">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="c6b20-131">Considérons, par exemple, les deux variables `sbyte` `x` et `y` suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6b20-131">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="c6b20-132">L’instruction d’assignation suivante entraîne une erreur de compilation, car l’expression arithmétique située à droite de l’opérateur d’assignation correspond à [int](../../../csharp/language-reference/keywords/int.md) par défaut.</span><span class="sxs-lookup"><span data-stu-id="c6b20-132">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="c6b20-133">Pour corriger ce problème, castez l’expression comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c6b20-133">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="c6b20-134">Il est cependant possible d’utiliser les instructions suivantes dans lesquelles la variable de destination a une taille de stockage égale ou supérieure :</span><span class="sxs-lookup"><span data-stu-id="c6b20-134">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="c6b20-135">Notez aussi qu’il n’existe pas de conversion implicite des types virgule flottante en `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="c6b20-135">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="c6b20-136">Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :</span><span class="sxs-lookup"><span data-stu-id="c6b20-136">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="c6b20-137">Pour plus d’informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="c6b20-137">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="c6b20-138">Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="c6b20-138">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c6b20-139">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c6b20-139">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c6b20-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6b20-140">See Also</span></span>  
 <xref:System.SByte>  
 [<span data-ttu-id="c6b20-141">Référence C#</span><span class="sxs-lookup"><span data-stu-id="c6b20-141">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c6b20-142">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c6b20-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c6b20-143">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="c6b20-143">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c6b20-144">Tableau des types intégraux</span><span class="sxs-lookup"><span data-stu-id="c6b20-144">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="c6b20-145">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="c6b20-145">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="c6b20-146">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="c6b20-146">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="c6b20-147">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="c6b20-147">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
