---
title: "Comment : concaténer plusieurs chaînes (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a><span data-ttu-id="45458-102">Comment : concaténer plusieurs chaînes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="45458-102">How to: Concatenate Multiple Strings (C# Programming Guide)</span></span>
<span data-ttu-id="45458-103">La *concaténation* consiste à ajouter une chaîne à la fin d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="45458-103">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="45458-104">Quand vous concaténez des littéraux de chaîne ou des constantes de chaîne en utilisant l’opérateur `+`, le compilateur crée une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="45458-104">When you concatenate string literals or string constants by using the `+` operator, the compiler creates a single string.</span></span> <span data-ttu-id="45458-105">Aucune concaténation d’exécution ne se produit.</span><span class="sxs-lookup"><span data-stu-id="45458-105">No run time concatenation occurs.</span></span> <span data-ttu-id="45458-106">Toutefois, les variables chaîne peuvent être concaténées uniquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="45458-106">However, string variables can be concatenated only at run time.</span></span> <span data-ttu-id="45458-107">Dans ce contexte, vous devez comprendre l’impact des diverses approches sur les performances.</span><span class="sxs-lookup"><span data-stu-id="45458-107">In this case, you should understand the performance implications of the various approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45458-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="45458-108">Example</span></span>  
 <span data-ttu-id="45458-109">L’exemple suivant indique comment fractionner un long littéral de chaîne en plus petites chaînes pour améliorer la lisibilité du code source.</span><span class="sxs-lookup"><span data-stu-id="45458-109">The following example shows how to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="45458-110">Les diverses parties seront concaténées en une chaîne unique lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="45458-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="45458-111">Il n’y a aucune incidence sur les performances d’exécution, quel que soit le nombre de chaînes impliquées.</span><span class="sxs-lookup"><span data-stu-id="45458-111">There is no run time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="45458-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="45458-112">Example</span></span>  
 <span data-ttu-id="45458-113">Pour concaténer des variables chaîne, vous pouvez utiliser l’opérateur `+` ou `+=`, ou la méthode <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45458-113">To concatenate string variables, you can use the `+` or `+=` operators, or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="45458-114">L’opérateur `+` est facile à utiliser et convient au code intuitif.</span><span class="sxs-lookup"><span data-stu-id="45458-114">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="45458-115">Même si vous utilisez plusieurs opérateurs + dans une instruction, le contenu de la chaîne est copié une seule fois.</span><span class="sxs-lookup"><span data-stu-id="45458-115">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="45458-116">Toutefois, si vous répétez plusieurs fois cette opération, par exemple dans une boucle, des problèmes d’efficacité peuvent se poser.</span><span class="sxs-lookup"><span data-stu-id="45458-116">But if you repeat this operation multiple times, for example in a loop, it might cause efficiency problems.</span></span> <span data-ttu-id="45458-117">Observez par exemple le code suivant :</span><span class="sxs-lookup"><span data-stu-id="45458-117">For example, note the following code:</span></span>  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="45458-118">Dans les opérations de concaténation de chaîne, le compilateur C# traite une chaîne null de la même manière qu’une chaîne vide, mais il ne convertit pas la valeur de la chaîne null d’origine.</span><span class="sxs-lookup"><span data-stu-id="45458-118">In string concatenation operations, the C# compiler treats a null string the same as an empty string, but it does not convert the value of the original null string.</span></span>  
  
 <span data-ttu-id="45458-119">Si vous ne concaténez pas un grand nombre de chaînes (par exemple, dans une boucle), l’incidence de ce code sur les performances ne sera probablement pas significative.</span><span class="sxs-lookup"><span data-stu-id="45458-119">If you are not concatenating large numbers of strings (for example, in a loop), the performance cost of this code is probably not significant.</span></span> <span data-ttu-id="45458-120">Cette remarque s’applique également aux méthodes <xref:System.String.Concat%2A?displayProperty=nameWithType> et <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45458-120">The same is true for the <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType> methods.</span></span>  
  
 <span data-ttu-id="45458-121">Toutefois, si les performances sont une considération importante, vous devez toujours utiliser la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes.</span><span class="sxs-lookup"><span data-stu-id="45458-121">However, when performance is important, you should always use the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span> <span data-ttu-id="45458-122">Le code suivant utilise la méthode <xref:System.Text.StringBuilder.Append%2A> de la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes sans l’effet de chaînage de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="45458-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings without the chaining effect of the `+` operator.</span></span>  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="45458-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45458-123">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="45458-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="45458-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="45458-125">Chaînes</span><span class="sxs-lookup"><span data-stu-id="45458-125">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
