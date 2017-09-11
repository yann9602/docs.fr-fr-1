---
title: "goto (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
dev_langs:
- CSharp
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
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
ms.openlocfilehash: cd298809ab883f425f3bb88239f2951ab98cc03e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="goto-c-reference"></a><span data-ttu-id="f9167-102">goto (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f9167-102">goto (C# Reference)</span></span>
<span data-ttu-id="f9167-103">L’instruction `goto` transfère le contrôle du programme directement à une instruction étiquetée.</span><span class="sxs-lookup"><span data-stu-id="f9167-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="f9167-104">Une utilisation courante de `goto` consiste à transférer le contrôle à une étiquette switch-case ou à l’étiquette par défaut d’une instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="f9167-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="f9167-105">L’instruction `goto` sert aussi à quitter des boucles fortement imbriquées.</span><span class="sxs-lookup"><span data-stu-id="f9167-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9167-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9167-106">Example</span></span>  
 <span data-ttu-id="f9167-107">L’exemple suivant montre comment utiliser `goto` dans une instruction [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="f9167-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 <span data-ttu-id="f9167-108">[!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f9167-108">[!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9167-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9167-109">Example</span></span>  
 <span data-ttu-id="f9167-110">L’exemple suivant montre comment utiliser `goto` pour quitter des boucles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="f9167-110">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 <span data-ttu-id="f9167-111">[!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f9167-111">[!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f9167-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f9167-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9167-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9167-113">See Also</span></span>  
 <span data-ttu-id="f9167-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f9167-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f9167-116">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="f9167-117">[GoTo, instruction](/cpp/cpp/goto-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="f9167-117">[goto Statement](/cpp/cpp/goto-statement-cpp) </span></span>  
 [<span data-ttu-id="f9167-118">Instructions de saut</span><span class="sxs-lookup"><span data-stu-id="f9167-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)

