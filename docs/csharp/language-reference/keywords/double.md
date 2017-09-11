---
title: "double (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- double
- double_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: 26
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
ms.openlocfilehash: d5588f8391157fb56a5e5067bb8e11f9269fe733
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="double-c-reference"></a><span data-ttu-id="011b8-102">double (référence C#)</span><span class="sxs-lookup"><span data-stu-id="011b8-102">double (C# Reference)</span></span>
<span data-ttu-id="011b8-103">Le mot clé `double` désigne un type simple qui stocke des valeurs à virgule flottante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="011b8-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="011b8-104">Le tableau suivant montre la précision et la plage approximative pour le type `double`.</span><span class="sxs-lookup"><span data-stu-id="011b8-104">The following table shows the precision and approximate range for the `double` type.</span></span>  
  
|<span data-ttu-id="011b8-105">Type</span><span class="sxs-lookup"><span data-stu-id="011b8-105">Type</span></span>|<span data-ttu-id="011b8-106">Plage approximative</span><span class="sxs-lookup"><span data-stu-id="011b8-106">Approximate range</span></span>|<span data-ttu-id="011b8-107">Précision</span><span class="sxs-lookup"><span data-stu-id="011b8-107">Precision</span></span>|<span data-ttu-id="011b8-108">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="011b8-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|<span data-ttu-id="011b8-109">De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="011b8-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="011b8-110">15 à 16 chiffres</span><span class="sxs-lookup"><span data-stu-id="011b8-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="011b8-111">Littéraux</span><span class="sxs-lookup"><span data-stu-id="011b8-111">Literals</span></span>  
 <span data-ttu-id="011b8-112">Par défaut, un littéral numérique réel sur le côté droit de l’opérateur d’assignation est traité comme `double`.</span><span class="sxs-lookup"><span data-stu-id="011b8-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="011b8-113">Toutefois, si vous souhaitez qu’un nombre entier soit traité comme `double`, utilisez le suffixe d ou D, par exemple :</span><span class="sxs-lookup"><span data-stu-id="011b8-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>  
  
```  
double x = 3D;  
```  
  
## <a name="conversions"></a><span data-ttu-id="011b8-114">Conversions</span><span class="sxs-lookup"><span data-stu-id="011b8-114">Conversions</span></span>  
 <span data-ttu-id="011b8-115">Vous pouvez combiner des types numériques intégraux et des types virgule flottante dans une expression.</span><span class="sxs-lookup"><span data-stu-id="011b8-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="011b8-116">Dans ce cas, les types intégraux sont convertis en types virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="011b8-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="011b8-117">L’évaluation de l’expression est exécutée d’après les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="011b8-117">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="011b8-118">Si l’un des types virgule flottante est `double`, l’expression prend la valeur `double`, ou [bool](../../../csharp/language-reference/keywords/bool.md) dans les expressions relationnelles ou booléennes.</span><span class="sxs-lookup"><span data-stu-id="011b8-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="011b8-119">S’il n’existe aucun type `double` dans l’expression, elle prend la valeur [float](../../../csharp/language-reference/keywords/float.md), ou [bool](../../../csharp/language-reference/keywords/bool.md) dans les expressions relationnelles ou booléennes.</span><span class="sxs-lookup"><span data-stu-id="011b8-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="011b8-120">Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :</span><span class="sxs-lookup"><span data-stu-id="011b8-120">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="011b8-121">Zéro positif et négatif.</span><span class="sxs-lookup"><span data-stu-id="011b8-121">Positive and negative zero.</span></span>  
  
-   <span data-ttu-id="011b8-122">Infini positif et négatif.</span><span class="sxs-lookup"><span data-stu-id="011b8-122">Positive and negative infinity.</span></span>  
  
-   <span data-ttu-id="011b8-123">Valeur NaN (N’est pas un nombre).</span><span class="sxs-lookup"><span data-stu-id="011b8-123">Not-a-Number value (NaN).</span></span>  
  
-   <span data-ttu-id="011b8-124">L’ensemble fini de valeurs différentes de zéro.</span><span class="sxs-lookup"><span data-stu-id="011b8-124">The finite set of nonzero values.</span></span>  
  
 <span data-ttu-id="011b8-125">Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de l’[IEEE](http://go.microsoft.com/fwlink/?LinkId=26269).</span><span class="sxs-lookup"><span data-stu-id="011b8-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="011b8-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="011b8-126">Example</span></span>  
 <span data-ttu-id="011b8-127">Dans l’exemple suivant, un [int](../../../csharp/language-reference/keywords/int.md), un [short](../../../csharp/language-reference/keywords/short.md), un [float](../../../csharp/language-reference/keywords/float.md)et un `double` sont ajoutés pour donner un résultat `double`.</span><span class="sxs-lookup"><span data-stu-id="011b8-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>  
  
 <span data-ttu-id="011b8-128">[!code-cs[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="011b8-128">[!code-cs[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="011b8-129">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="011b8-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="011b8-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="011b8-130">See Also</span></span>  
 <span data-ttu-id="011b8-131">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="011b8-131">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="011b8-132">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="011b8-132">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="011b8-133">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="011b8-133">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="011b8-134">[Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md) </span><span class="sxs-lookup"><span data-stu-id="011b8-134">[Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md) </span></span>  
 <span data-ttu-id="011b8-135">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="011b8-135">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="011b8-136">[Tableau des types virgule flottante](../../../csharp/language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="011b8-136">[Floating-Point Types Table](../../../csharp/language-reference/keywords/floating-point-types-table.md) </span></span>  
 <span data-ttu-id="011b8-137">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="011b8-137">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="011b8-138">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="011b8-138">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

