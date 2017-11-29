---
title: "float (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 846f132812fe90a285c81a020d440fc846f88b5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="float-c-reference"></a><span data-ttu-id="1764f-102">float (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1764f-102">float (C# Reference)</span></span>
<span data-ttu-id="1764f-103">Le mot clé `float` désigne un type simple qui stocke des valeurs à virgule flottante de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="1764f-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="1764f-104">Le tableau suivant montre la précision et la plage approximative pour le type `float`.</span><span class="sxs-lookup"><span data-stu-id="1764f-104">The following table shows the precision and approximate range for the `float` type.</span></span>  
  
|<span data-ttu-id="1764f-105">Type</span><span class="sxs-lookup"><span data-stu-id="1764f-105">Type</span></span>|<span data-ttu-id="1764f-106">Plage approximative</span><span class="sxs-lookup"><span data-stu-id="1764f-106">Approximate range</span></span>|<span data-ttu-id="1764f-107">Précision</span><span class="sxs-lookup"><span data-stu-id="1764f-107">Precision</span></span>|<span data-ttu-id="1764f-108">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1764f-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="1764f-109">-3,4 × 10<sup>38</sup> à +3,4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="1764f-109">-3.4 × 10<sup>38</sup>to +3.4 × 10<sup>38</sup></span></span>|<span data-ttu-id="1764f-110">7 chiffres</span><span class="sxs-lookup"><span data-stu-id="1764f-110">7 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="1764f-111">Littéraux</span><span class="sxs-lookup"><span data-stu-id="1764f-111">Literals</span></span>  
 <span data-ttu-id="1764f-112">Par défaut, un littéral numérique réel sur le côté droit de l’opérateur d’assignation est traité comme un [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="1764f-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="1764f-113">Par conséquent, pour initialiser une variable de type float, utilisez le suffixe `f` ou `F`, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1764f-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>  
  
```csharp
float x = 3.5F;  
```
  
 <span data-ttu-id="1764f-114">Si vous n’utilisez pas de suffixe dans la déclaration précédente, vous obtiendrez une erreur de compilation, puisque vous essayez de stocker une valeur [double](double.md) dans une variable `float`.</span><span class="sxs-lookup"><span data-stu-id="1764f-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="1764f-115">Conversions</span><span class="sxs-lookup"><span data-stu-id="1764f-115">Conversions</span></span>  
 <span data-ttu-id="1764f-116">Vous pouvez combiner des types numériques intégraux et des types virgule flottante dans une expression.</span><span class="sxs-lookup"><span data-stu-id="1764f-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="1764f-117">Dans ce cas, les types intégraux sont convertis en types virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="1764f-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="1764f-118">L’évaluation de l’expression est exécutée d’après les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="1764f-118">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="1764f-119">Si l’un des types virgule flottante est [double](double.md), l’expression prend la valeur [double](double.md) ou [bool](bool.md) dans les expressions relationnelles ou booléennes.</span><span class="sxs-lookup"><span data-stu-id="1764f-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md) or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="1764f-120">S’il n’existe aucun type [double](double.md) dans l’expression, elle prend la valeur `float` ou [bool](bool.md) dans les expressions relationnelles ou booléennes.</span><span class="sxs-lookup"><span data-stu-id="1764f-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float` or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="1764f-121">Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :</span><span class="sxs-lookup"><span data-stu-id="1764f-121">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="1764f-122">Zéro positif et négatif</span><span class="sxs-lookup"><span data-stu-id="1764f-122">Positive and negative zero</span></span>  
  
-   <span data-ttu-id="1764f-123">Infini positif et négatif</span><span class="sxs-lookup"><span data-stu-id="1764f-123">Positive and negative infinity</span></span>  
  
-   <span data-ttu-id="1764f-124">Valeur NaN (N’est pas un nombre)</span><span class="sxs-lookup"><span data-stu-id="1764f-124">Not-a-Number value (NaN)</span></span>  
  
-   <span data-ttu-id="1764f-125">L’ensemble fini de valeurs différentes de zéro</span><span class="sxs-lookup"><span data-stu-id="1764f-125">The finite set of nonzero values</span></span>  
  
 <span data-ttu-id="1764f-126">Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de l’[IEEE](http://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="1764f-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1764f-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="1764f-127">Example</span></span>  
 <span data-ttu-id="1764f-128">Dans l’exemple suivant, un [int](int.md), un [short](short.md) et un `float` sont inclus dans une expression mathématique produisant un résultat `float`.</span><span class="sxs-lookup"><span data-stu-id="1764f-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="1764f-129">(N’oubliez pas que `float` est un alias du type <xref:System.Single?displayProperty=nameWithType>.) Notez qu’il n’y a aucune valeur [double](double.md) dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="1764f-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1764f-130">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1764f-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1764f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1764f-131">See Also</span></span>  
 <xref:System.Single>  
 [<span data-ttu-id="1764f-132">Référence C#</span><span class="sxs-lookup"><span data-stu-id="1764f-132">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1764f-133">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1764f-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1764f-134">Cast et conversions de types</span><span class="sxs-lookup"><span data-stu-id="1764f-134">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="1764f-135">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="1764f-135">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="1764f-136">Tableau des types intégraux</span><span class="sxs-lookup"><span data-stu-id="1764f-136">Integral Types Table</span></span>](integral-types-table.md)  
 [<span data-ttu-id="1764f-137">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="1764f-137">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="1764f-138">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="1764f-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="1764f-139">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="1764f-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
