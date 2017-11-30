---
title: "goto (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords: goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aa12a7547cfcd4a2076b5b0a308139f8a823f482
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="goto-c-reference"></a><span data-ttu-id="4909f-102">goto (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4909f-102">goto (C# Reference)</span></span>
<span data-ttu-id="4909f-103">L’instruction `goto` transfère le contrôle du programme directement à une instruction étiquetée.</span><span class="sxs-lookup"><span data-stu-id="4909f-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="4909f-104">Une utilisation courante de `goto` consiste à transférer le contrôle à une étiquette switch-case ou à l’étiquette par défaut d’une instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="4909f-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="4909f-105">L’instruction `goto` sert aussi à quitter des boucles fortement imbriquées.</span><span class="sxs-lookup"><span data-stu-id="4909f-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4909f-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="4909f-106">Example</span></span>  
 <span data-ttu-id="4909f-107">L’exemple suivant montre comment utiliser `goto` dans une instruction [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="4909f-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="4909f-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="4909f-108">Example</span></span>  
 <span data-ttu-id="4909f-109">L’exemple suivant montre comment utiliser `goto` pour quitter des boucles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="4909f-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4909f-110">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4909f-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4909f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4909f-111">See Also</span></span>  
 [<span data-ttu-id="4909f-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="4909f-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4909f-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4909f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4909f-114">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="4909f-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4909f-115">GoTo, instruction</span><span class="sxs-lookup"><span data-stu-id="4909f-115">goto Statement</span></span>](/cpp/cpp/goto-statement-cpp)  
 [<span data-ttu-id="4909f-116">Instructions de saut</span><span class="sxs-lookup"><span data-stu-id="4909f-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
