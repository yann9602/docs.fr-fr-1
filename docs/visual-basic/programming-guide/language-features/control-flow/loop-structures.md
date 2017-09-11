---
title: (Visual Basic) de Structures de boucle | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- control flow, loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures
- statements [Visual Basic], loop
- Do statement, Do loops
- conditional statements, loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: eba728d782bb5a6259467fb48f738f35580049c0
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="3e869-102">Structures de boucle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e869-102">Loop Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="3e869-103">structures de boucle permettent d’exécuter une ou plusieurs lignes de code de façon répétée.</span><span class="sxs-lookup"><span data-stu-id="3e869-103"> loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="3e869-104">Vous pouvez répéter les instructions d’une structure de boucle jusqu'à ce qu’une condition est `True`, jusqu'à ce qu’une condition est `False`, un nombre de fois ou une seule fois pour chaque élément spécifié dans une collection.</span><span class="sxs-lookup"><span data-stu-id="3e869-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="3e869-105">L’illustration suivante montre une structure de boucle qui exécute un jeu d’instructions jusqu'à ce qu’une condition prenne la valeur true.</span><span class="sxs-lookup"><span data-stu-id="3e869-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="3e869-106">![Organigramme d’une boucle Do... Jusqu'à ce que la boucle](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="3e869-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="3e869-107">Exécution d’un ensemble d’instructions jusqu'à ce qu’une condition prenne la valeur true</span><span class="sxs-lookup"><span data-stu-id="3e869-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="3e869-108">Boucles while</span><span class="sxs-lookup"><span data-stu-id="3e869-108">While Loops</span></span>  
 <span data-ttu-id="3e869-109">The `While`... `End While` exécute un ensemble d’instructions tant que la condition spécifiée dans le `While` instruction est `True`.</span><span class="sxs-lookup"><span data-stu-id="3e869-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="3e869-110">Pour plus d’informations, consultez [tandis que... End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e869-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="3e869-111">Boucles Do</span><span class="sxs-lookup"><span data-stu-id="3e869-111">Do Loops</span></span>  
 <span data-ttu-id="3e869-112">The `Do`... `Loop` vous permet de tester une condition au début ou à la fin d’une structure de boucle.</span><span class="sxs-lookup"><span data-stu-id="3e869-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="3e869-113">Vous pouvez également spécifier s’il faut répéter la boucle tant que la condition est `True` ou jusqu'à ce qu’il devienne `True`.</span><span class="sxs-lookup"><span data-stu-id="3e869-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="3e869-114">Pour plus d’informations, consultez [faire... Instruction de boucle](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e869-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="3e869-115">Boucles for</span><span class="sxs-lookup"><span data-stu-id="3e869-115">For Loops</span></span>  
 <span data-ttu-id="3e869-116">The `For`... `Next` exécute la boucle un nombre défini de fois.</span><span class="sxs-lookup"><span data-stu-id="3e869-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="3e869-117">Elle utilise une variable de contrôle de boucle, également appelée un *compteur*, pour assurer le suivi des répétitions.</span><span class="sxs-lookup"><span data-stu-id="3e869-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="3e869-118">Vous spécifiez les valeurs initiales et finales de ce compteur, et vous pouvez éventuellement spécifier la quantité d’incrémentation d’une répétition à la suivante.</span><span class="sxs-lookup"><span data-stu-id="3e869-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="3e869-119">Pour plus d’informations, consultez la page [pour... L’instruction suivante](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e869-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="3e869-120">Boucles For Each</span><span class="sxs-lookup"><span data-stu-id="3e869-120">For Each Loops</span></span>  
 <span data-ttu-id="3e869-121">The `For Each`... `Next` exécute un ensemble d’instructions une fois pour chaque élément dans une collection.</span><span class="sxs-lookup"><span data-stu-id="3e869-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="3e869-122">Vous spécifiez la variable de contrôle de boucle, mais vous n’avez pas à déterminer le début ou de fin des valeurs pour qu’il.</span><span class="sxs-lookup"><span data-stu-id="3e869-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="3e869-123">Pour plus d’informations, consultez [For Each... L’instruction suivante](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e869-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e869-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e869-124">See Also</span></span>  
 <span data-ttu-id="3e869-125">[Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="3e869-125">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="3e869-126"> [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="3e869-126"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="3e869-127"> [Autres Structures de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="3e869-127"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span></span>  
<span data-ttu-id="3e869-128"> [Structures de contrôle imbriquées](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)</span><span class="sxs-lookup"><span data-stu-id="3e869-128"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)</span></span>
