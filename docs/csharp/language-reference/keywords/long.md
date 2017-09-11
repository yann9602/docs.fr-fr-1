---
title: "long (référence C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
dev_langs:
- CSharp
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
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
ms.openlocfilehash: 5f7d2d6a3d5781b4e120b8399c7206d4429dd98e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="long-c-reference"></a><span data-ttu-id="6d4da-102">long (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6d4da-102">long (C# Reference)</span></span>

<span data-ttu-id="6d4da-103">`long` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="6d4da-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="6d4da-104">Type</span><span class="sxs-lookup"><span data-stu-id="6d4da-104">Type</span></span>|<span data-ttu-id="6d4da-105">Plage</span><span class="sxs-lookup"><span data-stu-id="6d4da-105">Range</span></span>|<span data-ttu-id="6d4da-106">Taille</span><span class="sxs-lookup"><span data-stu-id="6d4da-106">Size</span></span>|<span data-ttu-id="6d4da-107">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6d4da-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`long`|<span data-ttu-id="6d4da-108">-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="6d4da-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="6d4da-109">Entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="6d4da-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="6d4da-110">Littéraux</span><span class="sxs-lookup"><span data-stu-id="6d4da-110">Literals</span></span> 

<span data-ttu-id="6d4da-111">Vous pouvez déclarer et initialiser une variable `long` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).</span><span class="sxs-lookup"><span data-stu-id="6d4da-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="6d4da-112">Dans l’exemple suivant, les entiers égaux à 4 294 967 296 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `long`.</span><span class="sxs-lookup"><span data-stu-id="6d4da-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>  
  
<span data-ttu-id="6d4da-113">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]</span><span class="sxs-lookup"><span data-stu-id="6d4da-113">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="6d4da-114">Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="6d4da-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="6d4da-115">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="6d4da-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="6d4da-116">À compter de C# 7, vous pouvez également utiliser le caractère de soulignement, `_`, comme séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6d4da-116">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="6d4da-117">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span><span class="sxs-lookup"><span data-stu-id="6d4da-117">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span></span>  
 
 <span data-ttu-id="6d4da-118">Les littéraux entiers peuvent également inclure un suffixe qui désigne le type.</span><span class="sxs-lookup"><span data-stu-id="6d4da-118">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="6d4da-119">Le suffixe `L` désigne un type `long`.</span><span class="sxs-lookup"><span data-stu-id="6d4da-119">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="6d4da-120">L’exemple suivant utilise le suffixe `L` pour désigner un entier long :</span><span class="sxs-lookup"><span data-stu-id="6d4da-120">The following example uses the `L` suffix to denote a long integer:</span></span>
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  <span data-ttu-id="6d4da-121">Vous pouvez aussi utiliser la lettre minuscule « l » comme suffixe.</span><span class="sxs-lookup"><span data-stu-id="6d4da-121">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="6d4da-122">Ceci génère cependant un avertissement du compilateur, car la lettre « l » peut être facilement confondue avec le chiffre « 1 ».</span><span class="sxs-lookup"><span data-stu-id="6d4da-122">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="6d4da-123">Utilisez « L » pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="6d4da-123">Use "L" for clarity.</span></span>  
  
 <span data-ttu-id="6d4da-124">Quand vous utilisez le suffixe `L`, le type du littéral entier est déterminé comme étant `long` ou [ulong](../../../csharp/language-reference/keywords/ulong.md), en fonction de sa taille.</span><span class="sxs-lookup"><span data-stu-id="6d4da-124">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="6d4da-125">Dans ce cas, le type est `long`, car le littéral est inférieur à la plage de [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="6d4da-125">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="6d4da-126">Le suffixe est souvent utilisé pour appeler des méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="6d4da-126">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="6d4da-127">Par exemple, les méthodes surchargées suivantes ont des paramètres de type `long` et [int](../../../csharp/language-reference/keywords/int.md) :</span><span class="sxs-lookup"><span data-stu-id="6d4da-127">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 <span data-ttu-id="6d4da-128">Le suffixe `L` garantit que la surcharge appropriée est appelée :</span><span class="sxs-lookup"><span data-stu-id="6d4da-128">The `L` suffix guarantees that the correct overload is called:</span></span>  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
<span data-ttu-id="6d4da-129">Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée :</span><span class="sxs-lookup"><span data-stu-id="6d4da-129">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="6d4da-130">int</span><span class="sxs-lookup"><span data-stu-id="6d4da-130">int</span></span>](int.md)
2. [<span data-ttu-id="6d4da-131">uint</span><span class="sxs-lookup"><span data-stu-id="6d4da-131">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="6d4da-132">ulong</span><span class="sxs-lookup"><span data-stu-id="6d4da-132">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 

<span data-ttu-id="6d4da-133">Dans l’exemple précédent, le littéral 4294967296 est de type `long`, car il dépasse la plage de [uint](../../../csharp/language-reference/keywords/uint.md) (consultez le [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour les tailles de stockage des types intégraux).</span><span class="sxs-lookup"><span data-stu-id="6d4da-133">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>  
  
 <span data-ttu-id="6d4da-134">Vous pouvez utiliser le type `long` avec d’autres types intégraux dans la même expression, l’expression est évaluée comme `long` (ou [bool](../../../csharp/language-reference/keywords/bool.md) dans le cas d’expressions relationnelles ou booléennes).</span><span class="sxs-lookup"><span data-stu-id="6d4da-134">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="6d4da-135">Par exemple, l’expression suivante s’évalue en `long` :</span><span class="sxs-lookup"><span data-stu-id="6d4da-135">For example, the following expression evaluates as `long`:</span></span>  
  
```csharp  
898L + 88  
```  
  
 <span data-ttu-id="6d4da-136">Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="6d4da-136">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="6d4da-137">Conversions</span><span class="sxs-lookup"><span data-stu-id="6d4da-137">Conversions</span></span>  
 <span data-ttu-id="6d4da-138">Il existe une conversion implicite prédéfinie de `long` en [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="6d4da-138">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="6d4da-139">Dans le cas contraire, vous devez utiliser un cast.</span><span class="sxs-lookup"><span data-stu-id="6d4da-139">Otherwise a cast must be used.</span></span> <span data-ttu-id="6d4da-140">Par exemple, l’instruction suivante génère une erreur de compilation sans un cast explicite :</span><span class="sxs-lookup"><span data-stu-id="6d4da-140">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 <span data-ttu-id="6d4da-141">Il existe une conversion implicite prédéfinie de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) vers `long`.</span><span class="sxs-lookup"><span data-stu-id="6d4da-141">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>  
  
 <span data-ttu-id="6d4da-142">Notez aussi qu’il n’existe pas de conversion implicite des types virgule flottante vers `long`.</span><span class="sxs-lookup"><span data-stu-id="6d4da-142">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="6d4da-143">Par exemple, l’instruction suivante génère une erreur du compilateur, sauf si vous utilisez un cast explicite :</span><span class="sxs-lookup"><span data-stu-id="6d4da-143">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="6d4da-144">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6d4da-144">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d4da-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d4da-145">See Also</span></span>  
 <span data-ttu-id="6d4da-146"><xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="6d4da-146"><xref:System.Int64></span></span>   
 <span data-ttu-id="6d4da-147">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d4da-147">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6d4da-148">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d4da-148">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6d4da-149">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d4da-149">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="6d4da-150">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="6d4da-150">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="6d4da-151">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="6d4da-151">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="6d4da-152">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="6d4da-152">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="6d4da-153">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="6d4da-153">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

