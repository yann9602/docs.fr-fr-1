---
title: "Guide pratique pour concaténer plusieurs chaînes (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 21
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
ms.openlocfilehash: b191a61258a496115a4d7045046f9b4a2dbee58c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a><span data-ttu-id="6f301-102">Guide pratique pour concaténer plusieurs chaînes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6f301-102">How to: Concatenate Multiple Strings (C# Programming Guide)</span></span>
<span data-ttu-id="6f301-103">La *concaténation* consiste à ajouter une chaîne à la fin d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="6f301-103">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="6f301-104">Quand vous concaténez des littéraux de chaîne ou des constantes de chaîne en utilisant l’opérateur `+`, le compilateur crée une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="6f301-104">When you concatenate string literals or string constants by using the `+` operator, the compiler creates a single string.</span></span> <span data-ttu-id="6f301-105">Aucune concaténation d’exécution ne se produit.</span><span class="sxs-lookup"><span data-stu-id="6f301-105">No run time concatenation occurs.</span></span> <span data-ttu-id="6f301-106">Toutefois, les variables chaîne peuvent être concaténées uniquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6f301-106">However, string variables can be concatenated only at run time.</span></span> <span data-ttu-id="6f301-107">Dans ce contexte, vous devez comprendre l’impact des diverses approches sur les performances.</span><span class="sxs-lookup"><span data-stu-id="6f301-107">In this case, you should understand the performance implications of the various approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f301-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f301-108">Example</span></span>  
 <span data-ttu-id="6f301-109">L’exemple suivant indique comment fractionner un long littéral de chaîne en plus petites chaînes pour améliorer la lisibilité du code source.</span><span class="sxs-lookup"><span data-stu-id="6f301-109">The following example shows how to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="6f301-110">Les diverses parties seront concaténées en une chaîne unique lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="6f301-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="6f301-111">Il n’y a aucune incidence sur les performances d’exécution, quel que soit le nombre de chaînes impliquées.</span><span class="sxs-lookup"><span data-stu-id="6f301-111">There is no run time performance cost regardless of the number of strings involved.</span></span>  
  
 <span data-ttu-id="6f301-112">[!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6f301-112">[!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f301-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f301-113">Example</span></span>  
 <span data-ttu-id="6f301-114">Pour concaténer des variables chaîne, vous pouvez utiliser l’opérateur `+` ou `+=`, ou la méthode <xref:System.String.Concat%2A?displayProperty=fullName>, <xref:System.String.Format%2A?displayProperty=fullName> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="6f301-114">To concatenate string variables, you can use the `+` or `+=` operators, or the <xref:System.String.Concat%2A?displayProperty=fullName>, <xref:System.String.Format%2A?displayProperty=fullName> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName> methods.</span></span> <span data-ttu-id="6f301-115">L’opérateur `+` est facile à utiliser et convient au code intuitif.</span><span class="sxs-lookup"><span data-stu-id="6f301-115">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="6f301-116">Même si vous utilisez plusieurs opérateurs + dans une instruction, le contenu de la chaîne est copié une seule fois.</span><span class="sxs-lookup"><span data-stu-id="6f301-116">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="6f301-117">Toutefois, si vous répétez plusieurs fois cette opération, par exemple dans une boucle, des problèmes d’efficacité peuvent se poser.</span><span class="sxs-lookup"><span data-stu-id="6f301-117">But if you repeat this operation multiple times, for example in a loop, it might cause efficiency problems.</span></span> <span data-ttu-id="6f301-118">Observez par exemple le code suivant :</span><span class="sxs-lookup"><span data-stu-id="6f301-118">For example, note the following code:</span></span>  
  
 <span data-ttu-id="6f301-119">[!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6f301-119">[!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f301-120">Dans les opérations de concaténation de chaîne, le compilateur C# traite une chaîne null de la même manière qu’une chaîne vide, mais il ne convertit pas la valeur de la chaîne null d’origine.</span><span class="sxs-lookup"><span data-stu-id="6f301-120">In string concatenation operations, the C# compiler treats a null string the same as an empty string, but it does not convert the value of the original null string.</span></span>  
  
 <span data-ttu-id="6f301-121">Si vous ne concaténez pas un grand nombre de chaînes (par exemple, dans une boucle), l’incidence de ce code sur les performances ne sera probablement pas significative.</span><span class="sxs-lookup"><span data-stu-id="6f301-121">If you are not concatenating large numbers of strings (for example, in a loop), the performance cost of this code is probably not significant.</span></span> <span data-ttu-id="6f301-122">Cette remarque s’applique également aux méthodes <xref:System.String.Concat%2A?displayProperty=fullName> et <xref:System.String.Format%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="6f301-122">The same is true for the <xref:System.String.Concat%2A?displayProperty=fullName> and <xref:System.String.Format%2A?displayProperty=fullName> methods.</span></span>  
  
 <span data-ttu-id="6f301-123">Toutefois, si les performances sont une considération importante, vous devez toujours utiliser la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes.</span><span class="sxs-lookup"><span data-stu-id="6f301-123">However, when performance is important, you should always use the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span> <span data-ttu-id="6f301-124">Le code suivant utilise la méthode <xref:System.Text.StringBuilder.Append%2A> de la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes sans l’effet de chaînage de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="6f301-124">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings without the chaining effect of the `+` operator.</span></span>  
  
 <span data-ttu-id="6f301-125">[!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="6f301-125">[!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f301-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f301-126">See Also</span></span>  
 <span data-ttu-id="6f301-127"><xref:System.String></span><span class="sxs-lookup"><span data-stu-id="6f301-127"><xref:System.String></span></span>   
 <span data-ttu-id="6f301-128"><xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="6f301-128"><xref:System.Text.StringBuilder></span></span>   
 <span data-ttu-id="6f301-129">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6f301-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="6f301-130">Chaînes</span><span class="sxs-lookup"><span data-stu-id="6f301-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

