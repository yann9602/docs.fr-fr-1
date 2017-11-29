---
title: "do (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords: do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d24078d3fb985f643fb66aa456900d03d2ff3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="do-c-reference"></a><span data-ttu-id="d8a50-102">do (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d8a50-102">do (C# Reference)</span></span>
<span data-ttu-id="d8a50-103">L’instruction `do` exécute une instruction ou un bloc d’instructions de manière répétée jusqu’à ce qu’une expression spécifiée corresponde à `false`.</span><span class="sxs-lookup"><span data-stu-id="d8a50-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="d8a50-104">Le corps de la boucle doit être placée entre accolades, `{}`, sauf si elle se compose d’une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="d8a50-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="d8a50-105">Dans ce cas, les accolades sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="d8a50-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8a50-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8a50-106">Example</span></span>  
 <span data-ttu-id="d8a50-107">Dans l’exemple suivant, les instructions de boucle `do-while` s’exécutent tant que la variable `x` est inférieure à 5.</span><span class="sxs-lookup"><span data-stu-id="d8a50-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 <span data-ttu-id="d8a50-108">Contrairement à une instruction [while](../../../csharp/language-reference/keywords/while.md), une boucle `do-while` est exécutée une fois avant que l’expression conditionnelle soit évaluée.</span><span class="sxs-lookup"><span data-stu-id="d8a50-108">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="d8a50-109">À tout endroit dans le bloc `do-while`, vous pouvez quitter la boucle à l’aide de l’instruction [break](../../../csharp/language-reference/keywords/break.md).</span><span class="sxs-lookup"><span data-stu-id="d8a50-109">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="d8a50-110">Vous pouvez passer directement à l’instruction d’évaluation de l’expression `while` à l’aide de l’instruction [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="d8a50-110">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="d8a50-111">Si l’expression `while` a la valeur true, l’exécution se poursuit à la première instruction dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="d8a50-111">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="d8a50-112">Si l’expression a la valeur false, l’exécution se poursuit à la première instruction après la boucle `do-while`.</span><span class="sxs-lookup"><span data-stu-id="d8a50-112">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="d8a50-113">Vous pouvez aussi quitter une boucle `do-while` à l’aide des instructions [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="d8a50-113">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d8a50-114">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d8a50-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d8a50-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8a50-115">See Also</span></span>  
 [<span data-ttu-id="d8a50-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d8a50-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d8a50-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d8a50-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d8a50-118">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="d8a50-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d8a50-119">do-while, instruction (C++)</span><span class="sxs-lookup"><span data-stu-id="d8a50-119">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="d8a50-120">Instructions d’itération</span><span class="sxs-lookup"><span data-stu-id="d8a50-120">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
