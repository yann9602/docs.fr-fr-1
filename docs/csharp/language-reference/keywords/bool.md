---
title: "bool (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
dev_langs:
- CSharp
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 30
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
ms.openlocfilehash: f3b7455ab6b0ec780afe7d81b2ff990d47a31d20
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="bool-c-reference"></a><span data-ttu-id="483e0-102">bool (référence C#)</span><span class="sxs-lookup"><span data-stu-id="483e0-102">bool (C# Reference)</span></span>
<span data-ttu-id="483e0-103">Le mot clé `bool` est un alias de <xref:System.Boolean?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="483e0-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=fullName>.</span></span> <span data-ttu-id="483e0-104">Il s’utilise pour déclarer des variables qui stockent les valeurs booléennes [true](../../../csharp/language-reference/keywords/true.md) et [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="483e0-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="483e0-105">Si vous avez besoin d’une variable booléenne qui peut également avoir la valeur `null`, utilisez `bool?`.</span><span class="sxs-lookup"><span data-stu-id="483e0-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="483e0-106">Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="483e0-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="483e0-107">Littéraux</span><span class="sxs-lookup"><span data-stu-id="483e0-107">Literals</span></span>  
 <span data-ttu-id="483e0-108">Vous pouvez assigner une valeur booléenne à une variable `bool`.</span><span class="sxs-lookup"><span data-stu-id="483e0-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="483e0-109">Vous pouvez également assigner à une variable `bool` une expression dont le résultat est une valeur `bool`.</span><span class="sxs-lookup"><span data-stu-id="483e0-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 <span data-ttu-id="483e0-110">[!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="483e0-110">[!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]</span></span>  
  
 <span data-ttu-id="483e0-111">La valeur par défaut d’une variable `bool` est `false`.</span><span class="sxs-lookup"><span data-stu-id="483e0-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="483e0-112">La valeur par défaut d’une variable `bool?` est `null`.</span><span class="sxs-lookup"><span data-stu-id="483e0-112">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="483e0-113">Conversions</span><span class="sxs-lookup"><span data-stu-id="483e0-113">Conversions</span></span>  
 <span data-ttu-id="483e0-114">Dans C++, une valeur de type `bool` peut être convertie en une valeur de type `int`. En d’autres termes, `false` équivaut à zéro et `true` équivaut à une valeur différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="483e0-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="483e0-115">Dans C#, il n’y a pas de conversion possible entre le type `bool` et les autres types.</span><span class="sxs-lookup"><span data-stu-id="483e0-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="483e0-116">Par exemple, l’instruction `if` suivante n’est pas valide dans C# :</span><span class="sxs-lookup"><span data-stu-id="483e0-116">For example, the following `if` statement is invalid in C#:</span></span>  
  
 <span data-ttu-id="483e0-117">[!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="483e0-117">[!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]</span></span>  
  
 <span data-ttu-id="483e0-118">Pour tester une variable du type `int`, vous devez la comparer explicitement à une valeur, telle que zéro, comme suit :</span><span class="sxs-lookup"><span data-stu-id="483e0-118">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 <span data-ttu-id="483e0-119">[!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="483e0-119">[!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="483e0-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="483e0-120">Example</span></span>  
 <span data-ttu-id="483e0-121">Dans cet exemple, vous tapez un caractère, et le programme vérifie si le caractère entré est une lettre.</span><span class="sxs-lookup"><span data-stu-id="483e0-121">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="483e0-122">Si c’est une lettre, le programme vérifie s’il s’agit d’une minuscule ou d’une majuscule.</span><span class="sxs-lookup"><span data-stu-id="483e0-122">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="483e0-123">Ces vérifications sont effectuées avec les méthodes <xref:System.Char.IsLetter%2A>, et <xref:System.Char.IsLower%2A>, qui retournent toutes les deux le type `bool` :</span><span class="sxs-lookup"><span data-stu-id="483e0-123">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 <span data-ttu-id="483e0-124">[!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="483e0-124">[!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="483e0-125">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="483e0-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="483e0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="483e0-126">See Also</span></span>  
 <span data-ttu-id="483e0-127">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="483e0-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="483e0-128">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="483e0-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="483e0-129">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="483e0-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="483e0-130">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="483e0-130">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="483e0-131">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="483e0-131">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="483e0-132">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="483e0-132">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="483e0-133">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="483e0-133">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

