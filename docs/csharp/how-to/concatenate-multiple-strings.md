---
title: "Guide pratique pour concaténer plusieurs chaînes (Guide C#)"
description: "Il existe plusieurs façons de concaténer des chaînes dans C#. Découvrez les options et les raisons de les choisir."
ms.date: 01/11/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4bc5e04edba48065746b96841b628ec5843c5e9
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="f140a-104">Guide pratique pour concaténer plusieurs chaînes (Guide C#)</span><span class="sxs-lookup"><span data-stu-id="f140a-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="f140a-105">La *concaténation* consiste à ajouter une chaîne à la fin d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="f140a-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="f140a-106">Vous concaténez les chaînes à l’aide de l’opérateur +.</span><span class="sxs-lookup"><span data-stu-id="f140a-106">You concatenate strings by using the + operator.</span></span> <span data-ttu-id="f140a-107">Pour les littéraux de chaîne et les constantes de chaîne, la concaténation se produit au moment de la compilation ; aucune concaténation ne se produit au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f140a-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="f140a-108">Pour les variables de chaîne, la concaténation se produit uniquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f140a-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="f140a-109">L’exemple suivant utilise la concaténation pour diviser un long littéral de chaîne en plus petites chaînes pour améliorer la lisibilité du code source.</span><span class="sxs-lookup"><span data-stu-id="f140a-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="f140a-110">Les diverses parties seront concaténées en une chaîne unique lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f140a-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="f140a-111">Il n’y a aucune incidence sur les performances d’exécution, quel que soit le nombre de chaînes impliquées.</span><span class="sxs-lookup"><span data-stu-id="f140a-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="f140a-112">Pour concaténer des variables de chaîne, vous pouvez utiliser les opérateurs `+` ou `+=`, l’[interpolation de chaînes](../tutorials/string-interpolation.md), ou les méthodes <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f140a-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../tutorials/string-interpolation.md) or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="f140a-113">L’opérateur `+` est facile à utiliser et convient au code intuitif.</span><span class="sxs-lookup"><span data-stu-id="f140a-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="f140a-114">Même si vous utilisez plusieurs opérateurs + dans une instruction, le contenu de la chaîne est copié une seule fois.</span><span class="sxs-lookup"><span data-stu-id="f140a-114">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="f140a-115">Le code suivant montre deux exemples où l’opérateur `+` est utilisé pour concaténer des chaînes :</span><span class="sxs-lookup"><span data-stu-id="f140a-115">The following code shows two examples of using the `+` operator to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="f140a-116">Dans certaines expressions, il est plus facile de concaténer des chaînes à l’aide de l’interpolation de chaînes, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f140a-116">In some expressions, it is easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="f140a-117">Dans les opérations de concaténation de chaîne, le compilateur C# traite une chaîne null de la même manière qu’une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="f140a-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="f140a-118">Les autres méthodes permettant de concaténer des chaînes sont <xref:System.String.Concat%2A?displayProperty=nameWithType> et <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f140a-118">Other methods to concatenate strings are <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f140a-119">Ces méthodes fonctionnent bien quand vous créez une chaîne à partir d’un petit nombre de chaînes de composant.</span><span class="sxs-lookup"><span data-stu-id="f140a-119">These methods work well when you are building a string from a small number of component strings.</span></span> <span data-ttu-id="f140a-120">Ces méthodes conviennent aussi parfaitement quand vous connaissez le nombre de chaînes qui constituent votre chaîne concaténée.</span><span class="sxs-lookup"><span data-stu-id="f140a-120">These methdos are also a great choice when you know the number of strings that make up your concatenated string.</span></span>

<span data-ttu-id="f140a-121">Dans d’autres cas, vous pouvez combiner des chaînes dans une boucle quand vous ne connaissez pas le nombre de chaînes sources que vous combinez et que le nombre réel de chaînes sources peut se révéler très grand.</span><span class="sxs-lookup"><span data-stu-id="f140a-121">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="f140a-122">La classe <xref:System.Text.StringBuilder> a été conçue pour ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="f140a-122">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="f140a-123">Le code suivant utilise la méthode <xref:System.Text.StringBuilder.Append%2A> de la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes.</span><span class="sxs-lookup"><span data-stu-id="f140a-123">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="f140a-124">Vous pouvez en savoir plus sur les [raisons de choisir la concaténation de chaînes ou la classe `StringBuilder`](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="f140a-124">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="f140a-125">Une autre option permettant de joindre les chaînes d’une collection consiste à utiliser [LINQ](../programming-guide/concepts/linq/index.md) et la méthode <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f140a-125">Another option to join strings from a collection is to use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f140a-126">Cette méthode combine les chaînes sources en utilisant une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="f140a-126">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="f140a-127">L’expression lambda effectue le travail d’ajouter chaque chaîne à l’accumulation existante.</span><span class="sxs-lookup"><span data-stu-id="f140a-127">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="f140a-128">L’exemple suivant combine un tableau de mots en ajoutant un espace entre chaque mot du tableau :</span><span class="sxs-lookup"><span data-stu-id="f140a-128">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]  


## <a name="see-also"></a><span data-ttu-id="f140a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f140a-129">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="f140a-130">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f140a-130">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="f140a-131">Chaînes</span><span class="sxs-lookup"><span data-stu-id="f140a-131">Strings</span></span>](../programming-guide/strings/index.md)
