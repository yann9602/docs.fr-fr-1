---
title: "byte (référence C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords: byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 231a491914071b1d43b5a8938e677be531726e75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="byte-c-reference"></a><span data-ttu-id="03274-102">byte (référence C#)</span><span class="sxs-lookup"><span data-stu-id="03274-102">byte (C# Reference)</span></span>

<span data-ttu-id="03274-103">`byte` désigne un type intégral qui stocke des valeurs comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="03274-103">`byte` denotes an integral type that stores values as indicated in the following table.</span></span>  
  
|<span data-ttu-id="03274-104">Type</span><span class="sxs-lookup"><span data-stu-id="03274-104">Type</span></span>|<span data-ttu-id="03274-105">Plage</span><span class="sxs-lookup"><span data-stu-id="03274-105">Range</span></span>|<span data-ttu-id="03274-106">Taille</span><span class="sxs-lookup"><span data-stu-id="03274-106">Size</span></span>|<span data-ttu-id="03274-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="03274-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`byte`|<span data-ttu-id="03274-108">0 à 255</span><span class="sxs-lookup"><span data-stu-id="03274-108">0 to 255</span></span>|<span data-ttu-id="03274-109">Entier 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="03274-109">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="03274-110">Littéraux</span><span class="sxs-lookup"><span data-stu-id="03274-110">Literals</span></span>  

 <span data-ttu-id="03274-111">Vous pouvez déclarer et initialiser une variable `byte` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="03274-111">You can declare and initialize a `byte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="03274-112">Si le littéral entier est en dehors de la plage autorisée pour le type `byte` (autrement dit, s’il est inférieur à <xref:System.Byte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Byte.MaxValue?displayProperty=nameWithType>), une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="03274-112">If the integer literal is outside the range of `byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="03274-113">Dans l’exemple suivant, les entiers égaux à 201 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis des valeurs [int](../../../csharp/language-reference/keywords/int.md) en `byte`.</span><span class="sxs-lookup"><span data-stu-id="03274-113">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `byte` values.</span></span>    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> <span data-ttu-id="03274-114">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="03274-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="03274-115">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="03274-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="03274-116">À partir de C# 7, quelques fonctionnalités ont été ajoutées améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="03274-116">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="03274-117">C# 7.0 permet l’utilisation d’un caractère de soulignement `_`, comme un séparateur de chiffre.</span><span class="sxs-lookup"><span data-stu-id="03274-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="03274-118">7.2 c# permet `_` à utiliser comme séparateur de chiffres pour un littéral binaire ou en hexadécimal, après le préfixe.</span><span class="sxs-lookup"><span data-stu-id="03274-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="03274-119">Un littéral décimal n’est pas autorisé à avoir un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="03274-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="03274-120">Certains exemples sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="03274-120">Some examples are shown below.</span></span>

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a><span data-ttu-id="03274-121">Conversions</span><span class="sxs-lookup"><span data-stu-id="03274-121">Conversions</span></span>  
 <span data-ttu-id="03274-122">Il y a une conversion implicite prédéfinie du type `byte` en [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="03274-122">There is a predefined implicit conversion from `byte` to [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="03274-123">Vous ne pouvez pas convertir implicitement en type `byte` des types numériques non littéraux ayant une taille de stockage supérieure.</span><span class="sxs-lookup"><span data-stu-id="03274-123">You cannot implicitly convert non-literal numeric types of larger storage size to `byte`.</span></span> <span data-ttu-id="03274-124">Pour plus d’informations sur les tailles de stockage des types intégraux, consultez [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="03274-124">For more information on the storage sizes of integral types, see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md).</span></span> <span data-ttu-id="03274-125">Observez l’exemple suivant qui utilise deux variables `byte`, `x` et `y` :</span><span class="sxs-lookup"><span data-stu-id="03274-125">Consider, for example, the following two `byte` variables `x` and `y`:</span></span>  
  
```  
byte x = 10, y = 20;  
```  
  
 <span data-ttu-id="03274-126">L’instruction d’assignation suivante entraîne une erreur de compilation, car l’expression arithmétique située à droite de l’opérateur d’assignation donne la valeur `int` par défaut.</span><span class="sxs-lookup"><span data-stu-id="03274-126">The following assignment statement will produce a compilation error, because the arithmetic expression on the right-hand side of the assignment operator evaluates to `int` by default.</span></span>  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 <span data-ttu-id="03274-127">Pour corriger ce problème, utilisez un cast :</span><span class="sxs-lookup"><span data-stu-id="03274-127">To fix this problem, use a cast:</span></span>  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 <span data-ttu-id="03274-128">Il est cependant possible d’utiliser les instructions suivantes, dans lesquelles la variable de destination a une taille de stockage égale ou supérieure :</span><span class="sxs-lookup"><span data-stu-id="03274-128">It is possible though, to use the following statements where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="03274-129">Il n’y a pas non plus de conversion implicite en `byte` pour les types virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="03274-129">Also, there is no implicit conversion from floating-point types to `byte`.</span></span> <span data-ttu-id="03274-130">Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :</span><span class="sxs-lookup"><span data-stu-id="03274-130">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 <span data-ttu-id="03274-131">Quand vous appelez des méthodes surchargées, vous devez utiliser un cast.</span><span class="sxs-lookup"><span data-stu-id="03274-131">When calling overloaded methods, a cast must be used.</span></span> <span data-ttu-id="03274-132">Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `byte` et [int](../../../csharp/language-reference/keywords/int.md) :</span><span class="sxs-lookup"><span data-stu-id="03274-132">Consider, for example, the following overloaded methods that use `byte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 <span data-ttu-id="03274-133">L’utilisation du cast `byte` garantit l’appel du type correct, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="03274-133">Using the `byte` cast guarantees that the correct type is called, for example:</span></span>  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 <span data-ttu-id="03274-134">Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="03274-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="03274-135">Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="03274-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="03274-136">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="03274-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="03274-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03274-137">See Also</span></span>  
 <xref:System.Byte>  
 [<span data-ttu-id="03274-138">Référence C#</span><span class="sxs-lookup"><span data-stu-id="03274-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="03274-139">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="03274-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="03274-140">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="03274-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="03274-141">Tableau des types intégraux</span><span class="sxs-lookup"><span data-stu-id="03274-141">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="03274-142">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="03274-142">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="03274-143">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="03274-143">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="03274-144">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="03274-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
