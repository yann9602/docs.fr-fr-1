---
title: "while (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
dev_langs:
- CSharp
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
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
ms.openlocfilehash: ed531c83dba02b38576bf8354b1ff92f075048bc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="while-c-reference"></a><span data-ttu-id="4caf7-102">while (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4caf7-102">while (C# Reference)</span></span>
<span data-ttu-id="4caf7-103">L’instruction `while` exécute une instruction ou un bloc d’instructions jusqu’à ce qu’une expression spécifique corresponde à la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="4caf7-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4caf7-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="4caf7-104">Example</span></span>  
 <span data-ttu-id="4caf7-105">[!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4caf7-105">[!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4caf7-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="4caf7-106">Example</span></span>  
 <span data-ttu-id="4caf7-107">[!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4caf7-107">[!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4caf7-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="4caf7-108">Example</span></span>  
 <span data-ttu-id="4caf7-109">Comme le test de l’expression `while` a lieu avant chaque exécution de la boucle, une boucle `while` est exécutée plusieurs fois ou pas du tout.</span><span class="sxs-lookup"><span data-stu-id="4caf7-109">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="4caf7-110">Cela diffère de la boucle [do](../../../csharp/language-reference/keywords/do.md), qui s’exécute une ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="4caf7-110">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="4caf7-111">Une boucle `while` peut être terminée quand une instruction [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md) transfère le contrôle à l’extérieur de la boucle.</span><span class="sxs-lookup"><span data-stu-id="4caf7-111">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="4caf7-112">Pour transmettre le contrôle à la prochaine itération sans sortir de la boucle, utilisez l’instruction [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="4caf7-112">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="4caf7-113">Notez la différence de sortie des trois exemples précédents, selon l’emplacement où `int n` est incrémenté.</span><span class="sxs-lookup"><span data-stu-id="4caf7-113">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="4caf7-114">Dans l’exemple ci-dessous, aucune sortie n’est générée.</span><span class="sxs-lookup"><span data-stu-id="4caf7-114">In the example below no output is generated.</span></span>  
  
 <span data-ttu-id="4caf7-115">[!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4caf7-115">[!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4caf7-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4caf7-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4caf7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4caf7-117">See Also</span></span>  
 <span data-ttu-id="4caf7-118">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4caf7-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4caf7-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4caf7-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4caf7-120">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="4caf7-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="4caf7-121">[while, instruction (C++)](/cpp/cpp/while-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="4caf7-121">[while Statement (C++)](/cpp/cpp/while-statement-cpp) </span></span>  
 [<span data-ttu-id="4caf7-122">Instructions d’itération</span><span class="sxs-lookup"><span data-stu-id="4caf7-122">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)

