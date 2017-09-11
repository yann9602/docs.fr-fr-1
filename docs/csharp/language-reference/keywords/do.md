---
title: "do (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
dev_langs:
- CSharp
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
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
ms.openlocfilehash: 58a9361c440bc1b17c5ab929ff7b45ba71ce50a4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="do-c-reference"></a><span data-ttu-id="6d657-102">do (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6d657-102">do (C# Reference)</span></span>
<span data-ttu-id="6d657-103">L’instruction `do` exécute une instruction ou un bloc d’instructions de manière répétée jusqu’à ce qu’une expression spécifiée corresponde à `false`.</span><span class="sxs-lookup"><span data-stu-id="6d657-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="6d657-104">Le corps de la boucle doit être placée entre accolades, `{}`, sauf si elle se compose d’une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="6d657-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="6d657-105">Dans ce cas, les accolades sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="6d657-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d657-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d657-106">Example</span></span>  
 <span data-ttu-id="6d657-107">Dans l’exemple suivant, les instructions de boucle `do-while` s’exécutent tant que la variable `x` est inférieure à 5.</span><span class="sxs-lookup"><span data-stu-id="6d657-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 <span data-ttu-id="6d657-108">[!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d657-108">[!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]</span></span>  
  
 <span data-ttu-id="6d657-109">Contrairement à une instruction [while](../../../csharp/language-reference/keywords/while.md), une boucle `do-while` est exécutée une fois avant que l’expression conditionnelle soit évaluée.</span><span class="sxs-lookup"><span data-stu-id="6d657-109">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="6d657-110">À tout endroit dans le bloc `do-while`, vous pouvez quitter la boucle à l’aide de l’instruction [break](../../../csharp/language-reference/keywords/break.md).</span><span class="sxs-lookup"><span data-stu-id="6d657-110">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="6d657-111">Vous pouvez passer directement à l’instruction d’évaluation de l’expression `while` à l’aide de l’instruction [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="6d657-111">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="6d657-112">Si l’expression `while` a la valeur true, l’exécution se poursuit à la première instruction dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="6d657-112">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="6d657-113">Si l’expression a la valeur false, l’exécution se poursuit à la première instruction après la boucle `do-while`.</span><span class="sxs-lookup"><span data-stu-id="6d657-113">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="6d657-114">Vous pouvez aussi quitter une boucle `do-while` à l’aide des instructions [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="6d657-114">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6d657-115">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6d657-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d657-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d657-116">See Also</span></span>  
 <span data-ttu-id="6d657-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d657-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6d657-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d657-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6d657-119">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d657-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="6d657-120">[do-while, instruction (C++)](/cpp/cpp/do-while-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="6d657-120">[do-while Statement (C++)](/cpp/cpp/do-while-statement-cpp) </span></span>  
 [<span data-ttu-id="6d657-121">Instructions d’itération</span><span class="sxs-lookup"><span data-stu-id="6d657-121">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)

