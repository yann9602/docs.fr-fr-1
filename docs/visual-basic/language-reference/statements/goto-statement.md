---
title: GoTo, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a><span data-ttu-id="69db1-102">GoTo, instruction</span><span class="sxs-lookup"><span data-stu-id="69db1-102">GoTo Statement</span></span>
<span data-ttu-id="69db1-103">Crée une branche inconditionnelle vers une ligne spécifiée d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="69db1-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69db1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69db1-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="69db1-105">Élément</span><span class="sxs-lookup"><span data-stu-id="69db1-105">Part</span></span>  
 `line`  
 <span data-ttu-id="69db1-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="69db1-106">Required.</span></span> <span data-ttu-id="69db1-107">Toute étiquette de ligne.</span><span class="sxs-lookup"><span data-stu-id="69db1-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69db1-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="69db1-108">Remarks</span></span>  
 <span data-ttu-id="69db1-109">La `GoTo` instruction peut créer une branche que vers des lignes dans la procédure dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="69db1-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="69db1-110">La ligne doit avoir une ligne d’étiquette qui `GoTo` peuvent faire référence.</span><span class="sxs-lookup"><span data-stu-id="69db1-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="69db1-111">Pour plus d’informations, consultez [Comment : instructions de l’étiquette](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="69db1-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69db1-112">`GoTo`instructions peuvent rendre le code difficile à lire et mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="69db1-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="69db1-113">Si possible, utilisez une structure de contrôle à la place.</span><span class="sxs-lookup"><span data-stu-id="69db1-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="69db1-114">Pour plus d’informations, consultez [flux de contrôle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="69db1-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="69db1-115">Vous ne pouvez pas utiliser un `GoTo` instruction branchement depuis l’extérieur un `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, ou `Using`... `End Using` vers une étiquette à l’intérieur.</span><span class="sxs-lookup"><span data-stu-id="69db1-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="69db1-116">Création de branche et Constructions Try</span><span class="sxs-lookup"><span data-stu-id="69db1-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="69db1-117">Dans un `Try`... `Catch`... `Finally` construction, les règles suivantes s’appliquent à la création de branche avec la `GoTo` instruction.</span><span class="sxs-lookup"><span data-stu-id="69db1-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="69db1-118">Bloc ou région</span><span class="sxs-lookup"><span data-stu-id="69db1-118">Block or region</span></span>|<span data-ttu-id="69db1-119">Création de branche à partir d’à l’extérieur</span><span class="sxs-lookup"><span data-stu-id="69db1-119">Branching in from outside</span></span>|<span data-ttu-id="69db1-120">Création de branche à partir d’à l’intérieur</span><span class="sxs-lookup"><span data-stu-id="69db1-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="69db1-121">`Try`bloc</span><span class="sxs-lookup"><span data-stu-id="69db1-121">`Try` block</span></span>|<span data-ttu-id="69db1-122">Uniquement à partir d’un `Catch` bloc de la même construction <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="69db1-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="69db1-123">Uniquement en dehors de la construction entière</span><span class="sxs-lookup"><span data-stu-id="69db1-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="69db1-124">`Catch`bloc</span><span class="sxs-lookup"><span data-stu-id="69db1-124">`Catch` block</span></span>|<span data-ttu-id="69db1-125">Jamais autorisé</span><span class="sxs-lookup"><span data-stu-id="69db1-125">Never allowed</span></span>|<span data-ttu-id="69db1-126">Uniquement en dehors de la construction entière, ou à la `Try` bloc de la même construction <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="69db1-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="69db1-127">`Finally`bloc</span><span class="sxs-lookup"><span data-stu-id="69db1-127">`Finally` block</span></span>|<span data-ttu-id="69db1-128">Jamais autorisé</span><span class="sxs-lookup"><span data-stu-id="69db1-128">Never allowed</span></span>|<span data-ttu-id="69db1-129">Jamais autorisé</span><span class="sxs-lookup"><span data-stu-id="69db1-129">Never allowed</span></span>|  
  
 <span data-ttu-id="69db1-130"><sup>1</sup> si un `Try`... `Catch`... `Finally` est imbriquée dans une autre, un `Catch` bloc peut créer de branche dans le `Try` bloc à son propre niveau d’imbrication, mais pas vers un autre `Try` bloc.</span><span class="sxs-lookup"><span data-stu-id="69db1-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="69db1-131">Imbriquée `Try`... `Catch`... `Finally` construction doit être entièrement contenue dans un `Try` ou `Catch` bloc de la construction dans laquelle elle est imbriquée.</span><span class="sxs-lookup"><span data-stu-id="69db1-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="69db1-132">L’illustration suivante montre une `Try` imbriquée dans une autre.</span><span class="sxs-lookup"><span data-stu-id="69db1-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="69db1-133">Les diverses branches entre les blocs des deux constructions sont indiquées comme valide ou non valide.</span><span class="sxs-lookup"><span data-stu-id="69db1-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="69db1-134">![Diagramme graphique de branchement dans des constructions Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="69db1-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="69db1-135">Branches correctes et incorrectes dans les constructions Try</span><span class="sxs-lookup"><span data-stu-id="69db1-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="69db1-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="69db1-136">Example</span></span>  
 <span data-ttu-id="69db1-137">L’exemple suivant utilise la `GoTo` instruction pour les étiquettes de ligne dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="69db1-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="69db1-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69db1-138">See Also</span></span>  
 [<span data-ttu-id="69db1-139">Do...Loop (instruction)</span><span class="sxs-lookup"><span data-stu-id="69db1-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="69db1-140">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="69db1-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="69db1-141">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="69db1-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="69db1-142">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="69db1-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="69db1-143">Select...Case (instruction)</span><span class="sxs-lookup"><span data-stu-id="69db1-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="69db1-144">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="69db1-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="69db1-145">While...End While (instruction)</span><span class="sxs-lookup"><span data-stu-id="69db1-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="69db1-146">With...End With (instruction)</span><span class="sxs-lookup"><span data-stu-id="69db1-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
