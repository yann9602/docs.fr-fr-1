---
title: "int (référence C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords: int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7acb8bb482ebf8f5c2b508e7cfd45b5b64aae3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="int-c-reference"></a><span data-ttu-id="26e83-102">int (référence C#)</span><span class="sxs-lookup"><span data-stu-id="26e83-102">int (C# Reference)</span></span>

<span data-ttu-id="26e83-103">`int` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="26e83-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="26e83-104">Type</span><span class="sxs-lookup"><span data-stu-id="26e83-104">Type</span></span>|<span data-ttu-id="26e83-105">Plage</span><span class="sxs-lookup"><span data-stu-id="26e83-105">Range</span></span>|<span data-ttu-id="26e83-106">Taille</span><span class="sxs-lookup"><span data-stu-id="26e83-106">Size</span></span>|<span data-ttu-id="26e83-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="26e83-107">.NET Framework type</span></span>|<span data-ttu-id="26e83-108">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="26e83-108">Default Value</span></span>|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|<span data-ttu-id="26e83-109">-2,147,483,648 en 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="26e83-109">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="26e83-110">Entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="26e83-110">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="26e83-111">0</span><span class="sxs-lookup"><span data-stu-id="26e83-111">0</span></span>|  
  
## <a name="literals"></a><span data-ttu-id="26e83-112">Littéraux</span><span class="sxs-lookup"><span data-stu-id="26e83-112">Literals</span></span>  
 
<span data-ttu-id="26e83-113">Vous pouvez déclarer et initialiser une variable `int` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="26e83-113">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="26e83-114">Si le littéral entier est en dehors de la plage autorisée pour le type `int` (autrement dit, s’il est inférieur à <xref:System.Int32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int32.MaxValue?displayProperty=nameWithType>), une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="26e83-114">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="26e83-115">Dans l’exemple suivant, les entiers égaux à 90 946 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `int`.</span><span class="sxs-lookup"><span data-stu-id="26e83-115">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="26e83-116">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="26e83-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="26e83-117">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="26e83-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="26e83-118">À partir de C# 7, quelques fonctionnalités ont été ajoutées améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="26e83-118">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="26e83-119">C# 7.0 permet l’utilisation d’un caractère de soulignement `_`, comme un séparateur de chiffre.</span><span class="sxs-lookup"><span data-stu-id="26e83-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="26e83-120">7.2 c# permet `_` à utiliser comme séparateur de chiffres pour un littéral binaire ou en hexadécimal, après le préfixe.</span><span class="sxs-lookup"><span data-stu-id="26e83-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="26e83-121">Un littéral décimal n’est pas autorisé à avoir un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="26e83-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="26e83-122">Certains exemples sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="26e83-122">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="26e83-123">Les littéraux entiers peuvent également inclure un suffixe désignant le type, bien qu’il n’existe aucun suffixe qui désigne le type `int`.</span><span class="sxs-lookup"><span data-stu-id="26e83-123">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="26e83-124">Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée :</span><span class="sxs-lookup"><span data-stu-id="26e83-124">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="26e83-125">uint</span><span class="sxs-lookup"><span data-stu-id="26e83-125">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="26e83-126">long</span><span class="sxs-lookup"><span data-stu-id="26e83-126">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="26e83-127">ulong</span><span class="sxs-lookup"><span data-stu-id="26e83-127">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="26e83-128">Dans ces exemples, le littéral 90946 est de type `int`.</span><span class="sxs-lookup"><span data-stu-id="26e83-128">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="26e83-129">Conversions</span><span class="sxs-lookup"><span data-stu-id="26e83-129">Conversions</span></span>  
 <span data-ttu-id="26e83-130">Il existe une conversion implicite prédéfinie de `int` en [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="26e83-130">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="26e83-131">Exemple :</span><span class="sxs-lookup"><span data-stu-id="26e83-131">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="26e83-132">Il existe une conversion implicite prédéfinie de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `int`.</span><span class="sxs-lookup"><span data-stu-id="26e83-132">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="26e83-133">Par exemple, l’instruction d’assignation suivante génère une erreur de compilation sans cast :</span><span class="sxs-lookup"><span data-stu-id="26e83-133">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="26e83-134">Remarquez également qu’il n’existe pas de conversion implicite des types virgule flottante en `int`.</span><span class="sxs-lookup"><span data-stu-id="26e83-134">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="26e83-135">Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :</span><span class="sxs-lookup"><span data-stu-id="26e83-135">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="26e83-136">Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="26e83-136">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="26e83-137">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="26e83-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="26e83-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26e83-138">See Also</span></span>  
 <xref:System.Int32>  
 [<span data-ttu-id="26e83-139">Référence C#</span><span class="sxs-lookup"><span data-stu-id="26e83-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="26e83-140">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="26e83-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="26e83-141">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="26e83-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="26e83-142">Tableau des types intégraux</span><span class="sxs-lookup"><span data-stu-id="26e83-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="26e83-143">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="26e83-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="26e83-144">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="26e83-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="26e83-145">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="26e83-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
