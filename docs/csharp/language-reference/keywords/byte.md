---
title: "byte (référence C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- byte
- byte_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: 19
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
ms.openlocfilehash: 8ef7494e2a8a1463d37cff77d1dacebec8182b66
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="byte-c-reference"></a><span data-ttu-id="ddb19-102">byte (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ddb19-102">byte (C# Reference)</span></span>

<span data-ttu-id="ddb19-103">`byte` désigne un type intégral qui stocke des valeurs comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="ddb19-103">`byte` denotes an integral type that stores values as indicated in the following table.</span></span>  
  
|<span data-ttu-id="ddb19-104">Type</span><span class="sxs-lookup"><span data-stu-id="ddb19-104">Type</span></span>|<span data-ttu-id="ddb19-105">Plage</span><span class="sxs-lookup"><span data-stu-id="ddb19-105">Range</span></span>|<span data-ttu-id="ddb19-106">Taille</span><span class="sxs-lookup"><span data-stu-id="ddb19-106">Size</span></span>|<span data-ttu-id="ddb19-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ddb19-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`byte`|<span data-ttu-id="ddb19-108">0 à 255</span><span class="sxs-lookup"><span data-stu-id="ddb19-108">0 to 255</span></span>|<span data-ttu-id="ddb19-109">Entier 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="ddb19-109">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="ddb19-110">Littéraux</span><span class="sxs-lookup"><span data-stu-id="ddb19-110">Literals</span></span>  

 <span data-ttu-id="ddb19-111">Vous pouvez déclarer et initialiser une variable `byte` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="ddb19-111">You can declare and initialize a `byte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="ddb19-112">Si le littéral entier est en dehors de la plage de `byte` (autrement dit, s’il est inférieur à <xref:System.Byte.MinValue?displayProperty=fullName> ou supérieur à <xref:System.Byte.MaxValue?displayProperty=fullName>), une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="ddb19-112">If the integer literal is outside the range of `byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=fullName> or greater than <xref:System.Byte.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span>

<span data-ttu-id="ddb19-113">Dans l’exemple suivant, les entiers égaux à 201 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis des valeurs [int](../../../csharp/language-reference/keywords/int.md) en `byte`.</span><span class="sxs-lookup"><span data-stu-id="ddb19-113">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `byte` values.</span></span>    
  
<span data-ttu-id="ddb19-114">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]</span><span class="sxs-lookup"><span data-stu-id="ddb19-114">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="ddb19-115">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="ddb19-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="ddb19-116">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="ddb19-116">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ddb19-117">À compter de C# 7, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ddb19-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="ddb19-118">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]</span><span class="sxs-lookup"><span data-stu-id="ddb19-118">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]</span></span>  
 
## <a name="conversions"></a><span data-ttu-id="ddb19-119">Conversions</span><span class="sxs-lookup"><span data-stu-id="ddb19-119">Conversions</span></span>  
 <span data-ttu-id="ddb19-120">Il y a une conversion implicite prédéfinie du type `byte` en [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="ddb19-120">There is a predefined implicit conversion from `byte` to [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="ddb19-121">Vous ne pouvez pas convertir implicitement en type `byte` des types numériques non littéraux ayant une taille de stockage supérieure.</span><span class="sxs-lookup"><span data-stu-id="ddb19-121">You cannot implicitly convert non-literal numeric types of larger storage size to `byte`.</span></span> <span data-ttu-id="ddb19-122">Pour plus d’informations sur les tailles de stockage des types intégraux, consultez [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="ddb19-122">For more information on the storage sizes of integral types, see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md).</span></span> <span data-ttu-id="ddb19-123">Prenez l’exemple des deux variables `byte`, `x` et `y` suivantes :</span><span class="sxs-lookup"><span data-stu-id="ddb19-123">Consider, for example, the following two `byte` variables `x` and `y`:</span></span>  
  
```  
byte x = 10, y = 20;  
```  
  
 <span data-ttu-id="ddb19-124">L’instruction d’assignation suivante entraîne une erreur de compilation, car l’expression arithmétique située à droite de l’opérateur d’assignation donne la valeur `int` par défaut.</span><span class="sxs-lookup"><span data-stu-id="ddb19-124">The following assignment statement will produce a compilation error, because the arithmetic expression on the right-hand side of the assignment operator evaluates to `int` by default.</span></span>  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 <span data-ttu-id="ddb19-125">Pour corriger ce problème, utilisez un cast :</span><span class="sxs-lookup"><span data-stu-id="ddb19-125">To fix this problem, use a cast:</span></span>  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 <span data-ttu-id="ddb19-126">Il est cependant possible d’utiliser les instructions suivantes, dans lesquelles la variable de destination a une taille de stockage égale ou supérieure :</span><span class="sxs-lookup"><span data-stu-id="ddb19-126">It is possible though, to use the following statements where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="ddb19-127">Il n’y a pas non plus de conversion implicite en `byte` pour les types virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="ddb19-127">Also, there is no implicit conversion from floating-point types to `byte`.</span></span> <span data-ttu-id="ddb19-128">Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :</span><span class="sxs-lookup"><span data-stu-id="ddb19-128">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 <span data-ttu-id="ddb19-129">Quand vous appelez des méthodes surchargées, vous devez utiliser un cast.</span><span class="sxs-lookup"><span data-stu-id="ddb19-129">When calling overloaded methods, a cast must be used.</span></span> <span data-ttu-id="ddb19-130">Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `byte` et [int](../../../csharp/language-reference/keywords/int.md) :</span><span class="sxs-lookup"><span data-stu-id="ddb19-130">Consider, for example, the following overloaded methods that use `byte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 <span data-ttu-id="ddb19-131">L’utilisation du cast `byte` garantit l’appel du type correct, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="ddb19-131">Using the `byte` cast guarantees that the correct type is called, for example:</span></span>  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 <span data-ttu-id="ddb19-132">Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="ddb19-132">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="ddb19-133">Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="ddb19-133">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ddb19-134">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ddb19-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ddb19-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddb19-135">See Also</span></span>  
 <span data-ttu-id="ddb19-136"><xref:System.Byte></span><span class="sxs-lookup"><span data-stu-id="ddb19-136"><xref:System.Byte></span></span>   
 <span data-ttu-id="ddb19-137">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ddb19-137">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ddb19-138">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ddb19-138">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ddb19-139">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ddb19-139">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="ddb19-140">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="ddb19-140">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="ddb19-141">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="ddb19-141">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="ddb19-142">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="ddb19-142">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="ddb19-143">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="ddb19-143">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

