---
title: "decimal (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- decimal_CSharpKeyword
- decimal
dev_langs:
- CSharp
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: 32
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
ms.openlocfilehash: 4c06d14f01302a21427845d0269fc8181a380914
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="decimal-c-reference"></a><span data-ttu-id="43778-102">decimal (référence C#)</span><span class="sxs-lookup"><span data-stu-id="43778-102">decimal (C# Reference)</span></span>
<span data-ttu-id="43778-103">Le mot clé `decimal` indique un type de données 128 bits.</span><span class="sxs-lookup"><span data-stu-id="43778-103">The `decimal` keyword indicates a 128-bit data type.</span></span> <span data-ttu-id="43778-104">Par rapport à d’autres types virgule flottante, le type `decimal` fournit une plus grande précision et une plage de valeurs plus réduite ; il est donc particulièrement approprié aux calculs financiers et monétaires.</span><span class="sxs-lookup"><span data-stu-id="43778-104">Compared to other floating-point types, the `decimal` type has more precision and a smaller range, which makes it appropriate for financial and monetary calculations.</span></span> <span data-ttu-id="43778-105">Le tableau suivant indique la plage de valeurs approximative et la précision fournies par le type `decimal`.</span><span class="sxs-lookup"><span data-stu-id="43778-105">The approximate range and precision for the `decimal` type are shown in the following table.</span></span>  
  
|<span data-ttu-id="43778-106">Type</span><span class="sxs-lookup"><span data-stu-id="43778-106">Type</span></span>|<span data-ttu-id="43778-107">Plage approximative</span><span class="sxs-lookup"><span data-stu-id="43778-107">Approximate Range</span></span>|<span data-ttu-id="43778-108">Précision</span><span class="sxs-lookup"><span data-stu-id="43778-108">Precision</span></span>|<span data-ttu-id="43778-109">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43778-109">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|<span data-ttu-id="43778-110">(-7,9 x 10<sup>28</sup> à 7,9 x 10<sup>28</sup>) / (10<sup>0</sup> à 10<sup>28</sup>)</span><span class="sxs-lookup"><span data-stu-id="43778-110">(-7.9 x 10<sup>28</sup> to 7.9 x 10<sup>28</sup>) / (10<sup>0</sup> to 10<sup>28</sup>)</span></span>|<span data-ttu-id="43778-111">28-29 chiffres significatifs</span><span class="sxs-lookup"><span data-stu-id="43778-111">28-29 significant digits</span></span>|<xref:System.Decimal?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="43778-112">Littéraux</span><span class="sxs-lookup"><span data-stu-id="43778-112">Literals</span></span>  
 <span data-ttu-id="43778-113">Si vous souhaitez qu'un littéral numérique réel soit considéré comme une valeur de type `decimal`, utilisez le suffixe m ou M, comme indiqué ci-après :</span><span class="sxs-lookup"><span data-stu-id="43778-113">If you want a numeric real literal to be treated as `decimal`, use the suffix m or M, for example:</span></span>  
  
```csharp
decimal myMoney = 300.5m;  
```  
  
 <span data-ttu-id="43778-114">Si le suffixe m n’est pas spécifié, le nombre est considéré comme une valeur de type [double](../../../csharp/language-reference/keywords/double.md) et génère une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="43778-114">Without the suffix m, the number is treated as a [double](../../../csharp/language-reference/keywords/double.md) and generates a compiler error.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="43778-115">Conversions</span><span class="sxs-lookup"><span data-stu-id="43778-115">Conversions</span></span>  
 <span data-ttu-id="43778-116">Les types intégraux sont convertis implicitement en type `decimal` et ont pour résultat une valeur de type `decimal`.</span><span class="sxs-lookup"><span data-stu-id="43778-116">The integral types are implicitly converted to `decimal` and the result evaluates to `decimal`.</span></span> <span data-ttu-id="43778-117">Par conséquent, vous pouvez initialiser une variable de type decimal avec un littéral d'entier, sans utiliser de suffixe, par exemple :</span><span class="sxs-lookup"><span data-stu-id="43778-117">Therefore you can initialize a decimal variable using an integer literal, without the suffix, as follows:</span></span>  
  
```csharp
decimal myMoney = 300;  
```  
  
 <span data-ttu-id="43778-118">Étant donné qu’il n’y a pas de conversion implicite entre les autres types virgule flottante et le type `decimal`, un cast doit être utilisé pour convertir ces types.</span><span class="sxs-lookup"><span data-stu-id="43778-118">There is no implicit conversion between other floating-point types and the `decimal` type; therefore, a cast must be used to convert between these two types.</span></span> <span data-ttu-id="43778-119">Exemple :</span><span class="sxs-lookup"><span data-stu-id="43778-119">For example:</span></span>  
  
```csharp
decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 <span data-ttu-id="43778-120">Vous pouvez aussi combiner, au sein d'une même expression, des types `decimal` et des types numériques intégraux.</span><span class="sxs-lookup"><span data-stu-id="43778-120">You can also mix `decimal` and numeric integral types in the same expression.</span></span> <span data-ttu-id="43778-121">En revanche, si vous combinez le type `decimal` avec les autres types virgule flottante sans spécifier de cast, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="43778-121">However, mixing `decimal` and other floating-point types without a cast causes a compilation error.</span></span>  
  
 <span data-ttu-id="43778-122">Pour plus d’informations sur les conversions numériques implicites, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="43778-122">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="43778-123">Pour plus d’informations sur les conversions numériques explicites, consultez [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="43778-123">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
## <a name="formatting-decimal-output"></a><span data-ttu-id="43778-124">Application d'un format à un résultat de type decimal</span><span class="sxs-lookup"><span data-stu-id="43778-124">Formatting Decimal Output</span></span>  
 <span data-ttu-id="43778-125">Vous pouvez appliquer un format à un résultat à l'aide de la méthode `String.Format`, ou de la méthode <xref:System.Console.Write%2A?displayProperty=fullName>, qui appelle `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="43778-125">You can format the results by using the `String.Format` method, or through the <xref:System.Console.Write%2A?displayProperty=fullName> method, which calls `String.Format()`.</span></span> <span data-ttu-id="43778-126">Le format monétaire est spécifié à l'aide du format de chaîne monétaire standard « C » ou « c », comme le montre le second exemple traité ultérieurement dans cet article.</span><span class="sxs-lookup"><span data-stu-id="43778-126">The currency format is specified by using the standard currency format string "C" or "c," as shown in the second example later in this article.</span></span> <span data-ttu-id="43778-127">Pour plus d'informations sur la méthode `String.Format`, consultez <xref:System.String.Format%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="43778-127">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=fullName>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43778-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="43778-128">Example</span></span>  
 <span data-ttu-id="43778-129">L’exemple suivant provoque une erreur du compilateur en essayant d’ajouter les variables [double](../../../csharp/language-reference/keywords/double.md) et `decimal`.</span><span class="sxs-lookup"><span data-stu-id="43778-129">The following example causes a compiler error by trying to add [double](../../../csharp/language-reference/keywords/double.md) and `decimal` variables.</span></span>  
  
```csharp  
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
```  
  
 <span data-ttu-id="43778-130">Le résultat est l'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="43778-130">The result is the following error:</span></span>  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 <span data-ttu-id="43778-131">Dans cet exemple, un `decimal` et un [int](../../../csharp/language-reference/keywords/int.md) sont combinés dans la même expression.</span><span class="sxs-lookup"><span data-stu-id="43778-131">In this example, a `decimal` and an [int](../../../csharp/language-reference/keywords/int.md) are mixed in the same expression.</span></span> <span data-ttu-id="43778-132">Le résultat est de type `decimal`.</span><span class="sxs-lookup"><span data-stu-id="43778-132">The result evaluates to the `decimal` type.</span></span>  
  
 <span data-ttu-id="43778-133">[!code-cs[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="43778-133">[!code-cs[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="43778-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="43778-134">Example</span></span>  
 <span data-ttu-id="43778-135">Dans cet exemple, le résultat est mis en forme à l'aide de la chaîne de format monétaire.</span><span class="sxs-lookup"><span data-stu-id="43778-135">In this example, the output is formatted by using the currency format string.</span></span> <span data-ttu-id="43778-136">Notez que la valeur `x` est arrondie, car le nombre de décimales excède 0,99 $.</span><span class="sxs-lookup"><span data-stu-id="43778-136">Notice that `x` is rounded because the decimal places exceed $0.99.</span></span> <span data-ttu-id="43778-137">La variable `y`, représentant le nombre maximal exact de chiffres, est affichée dans le format correct.</span><span class="sxs-lookup"><span data-stu-id="43778-137">The variable `y`, which represents the maximum exact digits, is displayed exactly in the correct format.</span></span>  
  
 <span data-ttu-id="43778-138">[!code-cs[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="43778-138">[!code-cs[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="43778-139">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="43778-139">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="43778-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43778-140">See Also</span></span>  
 <span data-ttu-id="43778-141"><xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="43778-141"><xref:System.Decimal></span></span>   
 <span data-ttu-id="43778-142">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="43778-142">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="43778-143">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="43778-143">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="43778-144">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="43778-144">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="43778-145">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="43778-145">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="43778-146">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="43778-146">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="43778-147">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="43778-147">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 <span data-ttu-id="43778-148">[Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="43778-148">[Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="43778-149">Chaînes de format numériques standard</span><span class="sxs-lookup"><span data-stu-id="43778-149">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)

