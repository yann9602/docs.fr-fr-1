---
title: Structures de boucle (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f813a555677e3828297c9c360b7a47217c39524
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="03bbd-102">Structures de boucle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03bbd-102">Loop Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="03bbd-103">structures de boucle permettent d’exécuter une ou plusieurs lignes de code de façon répétée.</span><span class="sxs-lookup"><span data-stu-id="03bbd-103"> loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="03bbd-104">Vous pouvez répéter les instructions d’une structure de boucle jusqu'à ce qu’une condition est `True`, jusqu'à ce qu’une condition est `False`, un nombre de fois, ou qu’une seule fois pour chaque élément spécifié dans une collection.</span><span class="sxs-lookup"><span data-stu-id="03bbd-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="03bbd-105">L’illustration suivante montre une structure de boucle qui exécute un ensemble d’instructions jusqu'à ce qu’une condition devienne true.</span><span class="sxs-lookup"><span data-stu-id="03bbd-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="03bbd-106">![Organigramme d’une boucle Do... Jusqu'à ce que la boucle](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="03bbd-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="03bbd-107">Un ensemble d’instructions en cours d’exécution jusqu'à ce qu’une condition devienne true</span><span class="sxs-lookup"><span data-stu-id="03bbd-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="03bbd-108">Boucles while</span><span class="sxs-lookup"><span data-stu-id="03bbd-108">While Loops</span></span>  
 <span data-ttu-id="03bbd-109">Le `While`... `End While` exécute un ensemble d’instructions tant que la condition spécifiée dans le `While` instruction est `True`.</span><span class="sxs-lookup"><span data-stu-id="03bbd-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="03bbd-110">Pour plus d’informations, consultez [tandis que... End While, instruction](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="03bbd-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="03bbd-111">Boucles Do</span><span class="sxs-lookup"><span data-stu-id="03bbd-111">Do Loops</span></span>  
 <span data-ttu-id="03bbd-112">Le `Do`... `Loop` construction vous permet de tester une condition au début ou à la fin d’une structure de boucle.</span><span class="sxs-lookup"><span data-stu-id="03bbd-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="03bbd-113">Vous pouvez également spécifier s’il faut répéter la boucle tant que la condition est `True` ou jusqu'à ce qu’il devienne `True`.</span><span class="sxs-lookup"><span data-stu-id="03bbd-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="03bbd-114">Pour plus d’informations, consultez [faire... Instruction de boucle](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="03bbd-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="03bbd-115">Pour les boucles</span><span class="sxs-lookup"><span data-stu-id="03bbd-115">For Loops</span></span>  
 <span data-ttu-id="03bbd-116">Le `For`... `Next` exécute la boucle un nombre défini de fois.</span><span class="sxs-lookup"><span data-stu-id="03bbd-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="03bbd-117">Elle utilise une variable de contrôle de boucle, également appelée un *compteur*, pour effectuer le suivi des répétitions.</span><span class="sxs-lookup"><span data-stu-id="03bbd-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="03bbd-118">Vous spécifiez le début et fin des valeurs de ce compteur, et vous pouvez éventuellement spécifier la quantité d’incrémentation d’une répétition à la suivante.</span><span class="sxs-lookup"><span data-stu-id="03bbd-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="03bbd-119">Pour plus d’informations, consultez [pour... L’instruction suivante](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="03bbd-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="03bbd-120">Boucles For Each</span><span class="sxs-lookup"><span data-stu-id="03bbd-120">For Each Loops</span></span>  
 <span data-ttu-id="03bbd-121">Le `For Each`... `Next` exécute un ensemble d’instructions une fois pour chaque élément dans une collection.</span><span class="sxs-lookup"><span data-stu-id="03bbd-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="03bbd-122">Vous spécifiez la variable de contrôle de boucle, mais vous n’avez pas déterminer le début ou de fin des valeurs pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="03bbd-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="03bbd-123">Pour plus d’informations, consultez [For Each... L’instruction suivante](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="03bbd-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03bbd-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03bbd-124">See Also</span></span>  
 [<span data-ttu-id="03bbd-125">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="03bbd-125">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="03bbd-126">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="03bbd-126">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="03bbd-127">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="03bbd-127">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="03bbd-128">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="03bbd-128">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
