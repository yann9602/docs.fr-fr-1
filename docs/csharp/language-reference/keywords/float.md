---
title: "float (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- float
- float_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: 24
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
ms.openlocfilehash: 2f1fb02f84de504112eee826dbee1275fa3ccb7a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="float-c-reference"></a><span data-ttu-id="8b620-102">float (référence C#)</span><span class="sxs-lookup"><span data-stu-id="8b620-102">float (C# Reference)</span></span>
<span data-ttu-id="8b620-103">Le mot clé `float` désigne un type simple qui stocke des valeurs à virgule flottante de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="8b620-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="8b620-104">Le tableau suivant montre la précision et la plage approximative pour le type `float`.</span><span class="sxs-lookup"><span data-stu-id="8b620-104">The following table shows the precision and approximate range for the `float` type.</span></span>  
  
|<span data-ttu-id="8b620-105">Type</span><span class="sxs-lookup"><span data-stu-id="8b620-105">Type</span></span>|<span data-ttu-id="8b620-106">Plage approximative</span><span class="sxs-lookup"><span data-stu-id="8b620-106">Approximate range</span></span>|<span data-ttu-id="8b620-107">Précision</span><span class="sxs-lookup"><span data-stu-id="8b620-107">Precision</span></span>|<span data-ttu-id="8b620-108">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8b620-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="8b620-109">-3,4 × 10<sup>38</sup> à +3,4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="8b620-109">-3.4 × 10<sup>38</sup>to +3.4 × 10<sup>38</sup></span></span>|<span data-ttu-id="8b620-110">7 chiffres</span><span class="sxs-lookup"><span data-stu-id="8b620-110">7 digits</span></span>|<xref:System.Single?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="8b620-111">Littéraux</span><span class="sxs-lookup"><span data-stu-id="8b620-111">Literals</span></span>  
 <span data-ttu-id="8b620-112">Par défaut, un littéral numérique réel sur le côté droit de l’opérateur d’assignation est traité comme un [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="8b620-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="8b620-113">Par conséquent, pour initialiser une variable de type float, utilisez le suffixe `f` ou `F`, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8b620-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>  
  
```csharp
float x = 3.5F;  
```
  
 <span data-ttu-id="8b620-114">Si vous n’utilisez pas de suffixe dans la déclaration précédente, vous obtiendrez une erreur de compilation, puisque vous essayez de stocker une valeur [double](double.md) dans une variable `float`.</span><span class="sxs-lookup"><span data-stu-id="8b620-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="8b620-115">Conversions</span><span class="sxs-lookup"><span data-stu-id="8b620-115">Conversions</span></span>  
 <span data-ttu-id="8b620-116">Vous pouvez combiner des types numériques intégraux et des types virgule flottante dans une expression.</span><span class="sxs-lookup"><span data-stu-id="8b620-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="8b620-117">Dans ce cas, les types intégraux sont convertis en types virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="8b620-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="8b620-118">L’évaluation de l’expression est exécutée d’après les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b620-118">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="8b620-119">Si l’un des types virgule flottante est [double](double.md), l’expression prend la valeur [double](double.md) ou [bool](bool.md) dans les expressions relationnelles ou booléennes.</span><span class="sxs-lookup"><span data-stu-id="8b620-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md) or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="8b620-120">S’il n’existe aucun type [double](double.md) dans l’expression, elle prend la valeur `float` ou [bool](bool.md) dans les expressions relationnelles ou booléennes.</span><span class="sxs-lookup"><span data-stu-id="8b620-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float` or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="8b620-121">Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :</span><span class="sxs-lookup"><span data-stu-id="8b620-121">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="8b620-122">Zéro positif et négatif</span><span class="sxs-lookup"><span data-stu-id="8b620-122">Positive and negative zero</span></span>  
  
-   <span data-ttu-id="8b620-123">Infini positif et négatif</span><span class="sxs-lookup"><span data-stu-id="8b620-123">Positive and negative infinity</span></span>  
  
-   <span data-ttu-id="8b620-124">Valeur NaN (N’est pas un nombre)</span><span class="sxs-lookup"><span data-stu-id="8b620-124">Not-a-Number value (NaN)</span></span>  
  
-   <span data-ttu-id="8b620-125">L’ensemble fini de valeurs différentes de zéro</span><span class="sxs-lookup"><span data-stu-id="8b620-125">The finite set of nonzero values</span></span>  
  
 <span data-ttu-id="8b620-126">Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de l’[IEEE](http://go.microsoft.com/fwlink/?LinkId=26269).</span><span class="sxs-lookup"><span data-stu-id="8b620-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b620-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b620-127">Example</span></span>  
 <span data-ttu-id="8b620-128">Dans l’exemple suivant, un [int](int.md), un [short](short.md) et un `float` sont inclus dans une expression mathématique produisant un résultat `float`.</span><span class="sxs-lookup"><span data-stu-id="8b620-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="8b620-129">(N’oubliez pas que `float` est un alias du type <xref:System.Single?displayProperty=fullName>.) Notez qu’il n’y a aucune valeur [double](double.md) dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="8b620-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=fullName> type.) Notice that there is no [double](double.md) in the expression.</span></span>  
  
 <span data-ttu-id="8b620-130">[!code-cs[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8b620-130">[!code-cs[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8b620-131">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8b620-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b620-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b620-132">See Also</span></span>  
 <span data-ttu-id="8b620-133"><xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="8b620-133"><xref:System.Single></span></span>   
 <span data-ttu-id="8b620-134">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8b620-134">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8b620-135">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8b620-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8b620-136">[Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="8b620-136">[Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span></span>  
 <span data-ttu-id="8b620-137">[Mots clés C#](index.md) </span><span class="sxs-lookup"><span data-stu-id="8b620-137">[C# Keywords](index.md) </span></span>  
 <span data-ttu-id="8b620-138">[Tableau des types intégraux](integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="8b620-138">[Integral Types Table](integral-types-table.md) </span></span>  
 <span data-ttu-id="8b620-139">[Tableau des types intégrés](built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="8b620-139">[Built-In Types Table](built-in-types-table.md) </span></span>  
 <span data-ttu-id="8b620-140">[Tableau des conversions numériques implicites](implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="8b620-140">[Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="8b620-141">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="8b620-141">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)

