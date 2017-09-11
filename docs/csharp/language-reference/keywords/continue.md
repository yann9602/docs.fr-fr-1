---
title: "continue (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- continue_CSharpKeyword
- continue
dev_langs:
- CSharp
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4a0dcedb32b153c31ec5ed799f66062463307db9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="continue-c-reference"></a><span data-ttu-id="8a4b1-102">continue (référence C#)</span><span class="sxs-lookup"><span data-stu-id="8a4b1-102">continue (C# Reference)</span></span>
<span data-ttu-id="8a4b1-103">L’instruction `continue` passe le contrôle à l’itération suivante de l’instruction [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md) ou [foreach](../../../csharp/language-reference/keywords/foreach-in.md) englobante dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="8a4b1-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a4b1-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a4b1-104">Example</span></span>  
 <span data-ttu-id="8a4b1-105">Dans cet exemple, un compteur est initialisé pour compter de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="8a4b1-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="8a4b1-106">Si vous utilisez l’instruction `continue` conjointement avec l’expression `(i < 9)`, les instructions entre `continue` et la fin du corps de `for` sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="8a4b1-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>  
  
 <span data-ttu-id="8a4b1-107">[!code-cs[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8a4b1-107">[!code-cs[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8a4b1-108">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8a4b1-108">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8a4b1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a4b1-109">See Also</span></span>  
 <span data-ttu-id="8a4b1-110">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8a4b1-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8a4b1-111">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8a4b1-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8a4b1-112">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="8a4b1-112">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="8a4b1-113">[break, instruction](/cpp/cpp/break-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="8a4b1-113">[break Statement](/cpp/cpp/break-statement-cpp) </span></span>  
 [<span data-ttu-id="8a4b1-114">Instructions de saut</span><span class="sxs-lookup"><span data-stu-id="8a4b1-114">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)

