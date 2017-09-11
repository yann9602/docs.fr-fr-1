---
title: "short (référence C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
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
ms.openlocfilehash: ab3ccfdeb8d8a67b5fcd60b1ad6eee4dcafc9691
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="short-c-reference"></a><span data-ttu-id="f5b23-102">short (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f5b23-102">short (C# Reference)</span></span>

<span data-ttu-id="f5b23-103">`short` désigne un type de données intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f5b23-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="f5b23-104">Type</span><span class="sxs-lookup"><span data-stu-id="f5b23-104">Type</span></span>|<span data-ttu-id="f5b23-105">Plage</span><span class="sxs-lookup"><span data-stu-id="f5b23-105">Range</span></span>|<span data-ttu-id="f5b23-106">Taille</span><span class="sxs-lookup"><span data-stu-id="f5b23-106">Size</span></span>|<span data-ttu-id="f5b23-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f5b23-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`short`|<span data-ttu-id="f5b23-108">de -32 768 à 32 767</span><span class="sxs-lookup"><span data-stu-id="f5b23-108">-32,768 to 32,767</span></span>|<span data-ttu-id="f5b23-109">Entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="f5b23-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="f5b23-110">Littéraux</span><span class="sxs-lookup"><span data-stu-id="f5b23-110">Literals</span></span>  

<span data-ttu-id="f5b23-111">Vous pouvez déclarer et initialiser une variable `short` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="f5b23-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="f5b23-112">Si le littéral entier est en dehors de la plage de `short` (autrement dit, s’il est inférieur à <xref:System.Int16.MinValue?displayProperty=fullName> ou supérieur à <xref:System.Int16.MaxValue?displayProperty=fullName>), une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="f5b23-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=fullName> or greater than <xref:System.Int16.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span> 

<span data-ttu-id="f5b23-113">Dans l’exemple suivant, les entiers égaux à 1 034 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis à partir de valeurs [int](../../../csharp/language-reference/keywords/int.md) en `short`.</span><span class="sxs-lookup"><span data-stu-id="f5b23-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `short` values.</span></span>  
  
<span data-ttu-id="f5b23-114">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]</span><span class="sxs-lookup"><span data-stu-id="f5b23-114">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="f5b23-115">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="f5b23-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="f5b23-116">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="f5b23-116">Decimal literals have no prefix.</span></span>

<span data-ttu-id="f5b23-117">À compter de C# 7, vous pouvez également utiliser le caractère de soulignement, `_`, comme séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f5b23-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="f5b23-118">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]</span><span class="sxs-lookup"><span data-stu-id="f5b23-118">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]</span></span>  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="f5b23-119">Résolution de surcharge du compilateur</span><span class="sxs-lookup"><span data-stu-id="f5b23-119">Compiler overload resolution</span></span>

 <span data-ttu-id="f5b23-120">Un cast doit être utilisé lors de l’appel de méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="f5b23-120">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="f5b23-121">Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `short` et [int](../../../csharp/language-reference/keywords/int.md) :</span><span class="sxs-lookup"><span data-stu-id="f5b23-121">Consider, for example, the following overloaded methods that use `short` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 <span data-ttu-id="f5b23-122">L’utilisation du cast `short` garantit l’appel du type correct, par exemple :</span><span class="sxs-lookup"><span data-stu-id="f5b23-122">Using the `short` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="f5b23-123">Conversions</span><span class="sxs-lookup"><span data-stu-id="f5b23-123">Conversions</span></span>  

 <span data-ttu-id="f5b23-124">Il existe une conversion implicite prédéfinie de `short` en [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="f5b23-124">There is a predefined implicit conversion from `short` to [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="f5b23-125">Vous ne pouvez pas convertir implicitement des types numériques non littéraux de taille de stockage supérieure à `short` (consultez le [tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour voir les tailles de stockage des types intégraux).</span><span class="sxs-lookup"><span data-stu-id="f5b23-125">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="f5b23-126">Prenez l’exemple des deux variables `short``x` et `y` suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5b23-126">Consider, for example, the following two `short` variables `x` and `y`:</span></span>  
  
```csharp  
short x = 5, y = 12;  
```  
  
 <span data-ttu-id="f5b23-127">L’instruction d’assignation suivante entraîne une erreur de compilation, car l’expression arithmétique située à droite de l’opérateur d’assignation donne la valeur [int](../../../csharp/language-reference/keywords/int.md) par défaut.</span><span class="sxs-lookup"><span data-stu-id="f5b23-127">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 <span data-ttu-id="f5b23-128">Pour corriger ce problème, utilisez un cast :</span><span class="sxs-lookup"><span data-stu-id="f5b23-128">To fix this problem, use a cast:</span></span>  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 <span data-ttu-id="f5b23-129">Il est toutefois possible d’utiliser les instructions suivantes, dans lesquelles la variable de destination a une taille de stockage égale ou supérieure :</span><span class="sxs-lookup"><span data-stu-id="f5b23-129">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="f5b23-130">Il n’existe pas de conversion implicite des types virgule flottante en `short`.</span><span class="sxs-lookup"><span data-stu-id="f5b23-130">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="f5b23-131">Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :</span><span class="sxs-lookup"><span data-stu-id="f5b23-131">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 <span data-ttu-id="f5b23-132">Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="f5b23-132">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="f5b23-133">Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="f5b23-133">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f5b23-134">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f5b23-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5b23-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5b23-135">See Also</span></span>  
 <span data-ttu-id="f5b23-136"><xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="f5b23-136"><xref:System.Int16></span></span>   
 <span data-ttu-id="f5b23-137">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5b23-137">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f5b23-138">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5b23-138">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f5b23-139">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5b23-139">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="f5b23-140">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="f5b23-140">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="f5b23-141">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="f5b23-141">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="f5b23-142">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="f5b23-142">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="f5b23-143">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="f5b23-143">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

