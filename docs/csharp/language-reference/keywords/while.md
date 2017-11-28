---
title: "while (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords: while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a><span data-ttu-id="83245-102">while (référence C#)</span><span class="sxs-lookup"><span data-stu-id="83245-102">while (C# Reference)</span></span>
<span data-ttu-id="83245-103">L’instruction `while` exécute une instruction ou un bloc d’instructions jusqu’à ce qu’une expression spécifique corresponde à la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="83245-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83245-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="83245-104">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="83245-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="83245-105">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="83245-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="83245-106">Example</span></span>  
 <span data-ttu-id="83245-107">Comme le test de l’expression `while` a lieu avant chaque exécution de la boucle, une boucle `while` est exécutée plusieurs fois ou pas du tout.</span><span class="sxs-lookup"><span data-stu-id="83245-107">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="83245-108">Cela diffère de la boucle [do](../../../csharp/language-reference/keywords/do.md), qui s’exécute une ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="83245-108">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="83245-109">Une boucle `while` peut être terminée quand une instruction [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md) transfère le contrôle à l’extérieur de la boucle.</span><span class="sxs-lookup"><span data-stu-id="83245-109">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="83245-110">Pour transmettre le contrôle à la prochaine itération sans sortir de la boucle, utilisez l’instruction [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="83245-110">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="83245-111">Notez la différence de sortie des trois exemples précédents, selon l’emplacement où `int n` est incrémenté.</span><span class="sxs-lookup"><span data-stu-id="83245-111">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="83245-112">Dans l’exemple ci-dessous, aucune sortie n’est générée.</span><span class="sxs-lookup"><span data-stu-id="83245-112">In the example below no output is generated.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="83245-113">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="83245-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83245-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83245-114">See Also</span></span>  
 [<span data-ttu-id="83245-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="83245-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="83245-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="83245-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="83245-117">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="83245-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="83245-118">while, instruction (C++)</span><span class="sxs-lookup"><span data-stu-id="83245-118">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="83245-119">Instructions d’itération</span><span class="sxs-lookup"><span data-stu-id="83245-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
