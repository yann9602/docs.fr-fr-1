---
title: If...Then...Else, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 898b72055345e88ca35f805de211c0c57cd74200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="1ae5a-102">If...Then...Else, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ae5a-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="1ae5a-103">Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ae5a-104">Syntax</span></span>  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="1ae5a-105">Composants</span><span class="sxs-lookup"><span data-stu-id="1ae5a-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="1ae5a-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-106">Required.</span></span> <span data-ttu-id="1ae5a-107">Expression.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-107">Expression.</span></span> <span data-ttu-id="1ae5a-108">Doit correspondre à `True` ou `False`, ou à un type de données qui est implicitement convertible en `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-108">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="1ae5a-109">Si l’expression est un [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable qui prend la valeur [rien](../../../visual-basic/language-reference/nothing.md), la condition est traitée comme si l’expression n’est pas `True`et le `Else` bloc exécutée.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-109">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is not `True`, and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="1ae5a-110">Requis dans la syntaxe de ligne ; facultatif dans la syntaxe de plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-110">Required in the single-line syntax; optional in the multiple-line syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="1ae5a-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-111">Optional.</span></span> <span data-ttu-id="1ae5a-112">Une ou plusieurs instructions qui suivent `If`... `Then` sont exécutées si `condition` prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-112">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="1ae5a-113">Obligatoire si `ElseIf` est présent.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-113">Required if `ElseIf` is present.</span></span> <span data-ttu-id="1ae5a-114">Expression.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-114">Expression.</span></span> <span data-ttu-id="1ae5a-115">Doit correspondre à `True` ou `False`, ou à un type de données qui est implicitement convertible en `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-115">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="1ae5a-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-116">Optional.</span></span> <span data-ttu-id="1ae5a-117">Une ou plusieurs instructions qui suivent `ElseIf`... `Then` sont exécutées si `elseifcondition` prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-117">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="1ae5a-118">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-118">Optional.</span></span> <span data-ttu-id="1ae5a-119">Une ou plusieurs instructions sont exécutées si aucune `condition` ou `elseifcondition` expression renvoie la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-119">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="1ae5a-120">Met fin à la `If`... `Then`... `Else` bloc.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-120">Terminates the `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ae5a-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="1ae5a-121">Remarks</span></span>  
  
## <a name="multiple-line-syntax"></a><span data-ttu-id="1ae5a-122">Syntaxe sur plusieurs lignes</span><span class="sxs-lookup"><span data-stu-id="1ae5a-122">Multiple-Line Syntax</span></span>  
 <span data-ttu-id="1ae5a-123">Lorsqu’un `If`... `Then`... `Else` est rencontrée, `condition` est testée.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-123">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="1ae5a-124">Si `condition` est `True`, les instructions qui suivent `Then` sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-124">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="1ae5a-125">Si `condition` est `False`, chaque `ElseIf` instruction (le cas échéant) est évaluée dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-125">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="1ae5a-126">Lorsqu’un `True``elseifcondition` est trouvée, les instructions qui suit immédiatement la `ElseIf` sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-126">When a `True``elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="1ae5a-127">Si aucun `elseifcondition` prend la valeur de `True`, ou s’il n’y a aucune `ElseIf` instructions, les instructions qui suivent `Else` sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-127">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="1ae5a-128">Après l’exécution d’instructions qui suivent `Then`, `ElseIf`, ou `Else`, l’exécution se poursuit avec l’instruction qui suit `End If`.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-128">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="1ae5a-129">Le `ElseIf` et `Else` clauses sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-129">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="1ae5a-130">Vous pouvez avoir autant `ElseIf` clauses que vous souhaitez dans un `If`... `Then`... `Else` instruction, mais pas `ElseIf` clause peut apparaître après une `Else` clause.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-130">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="1ae5a-131">`If`... `Then`... `Else` instructions peuvent être imbriquées dans d’autres.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-131">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="1ae5a-132">Dans la syntaxe de plusieurs lignes, la `If` instruction doit être la seule instruction sur la première ligne.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-132">In the multiple-line syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="1ae5a-133">Le `ElseIf`, `Else`, et `End If` instructions peuvent être précédées que par une étiquette de ligne.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-133">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="1ae5a-134">Le `If`... `Then`... `Else` doit se terminer par un `End If` instruction.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-134">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="1ae5a-135">Le [sélectionnez... Cas d’instruction](../../../visual-basic/language-reference/statements/select-case-statement.md) peuvent être plus utiles lorsque vous évaluez une expression unique qui possède plusieurs valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-135">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
## <a name="single-line-syntax"></a><span data-ttu-id="1ae5a-136">Syntaxe de ligne</span><span class="sxs-lookup"><span data-stu-id="1ae5a-136">Single-Line Syntax</span></span>  
 <span data-ttu-id="1ae5a-137">Vous pouvez utiliser la syntaxe d’une ligne pour les tests courts et simples.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-137">You can use the single-line syntax for short, simple tests.</span></span> <span data-ttu-id="1ae5a-138">Toutefois, la syntaxe de plusieurs lignes offre plus de souplesse et de structure et est généralement plus facile à lire, mettre à jour et le débogage.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-138">However, the multiple-line syntax provides more structure and flexibility and is usually easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="1ae5a-139">Ce qui suit le `Then` mot clé est examinée pour déterminer si une instruction est une seule ligne `If`.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-139">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="1ae5a-140">Si l’autre chose qu’un commentaire apparaît après `Then` sur la même ligne, l’instruction est traitée comme une seule ligne `If` instruction.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-140">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="1ae5a-141">Si `Then` est absent, il doit être le début d’une ligne de plusieurs `If`... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-141">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="1ae5a-142">Dans la syntaxe de ligne simple, vous pouvez avoir plusieurs instructions exécutées en tant que le résultat d’une `If`... `Then` décision.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-142">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="1ae5a-143">Toutes les instructions doivent se trouver sur la même ligne et être séparées par un signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-143">All statements must be on the same line and be separated by colons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ae5a-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ae5a-144">Example</span></span>  
 <span data-ttu-id="1ae5a-145">L’exemple suivant illustre l’utilisation de la syntaxe de plusieurs lignes de la `If`... `Then`... `Else` instruction.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-145">The following example illustrates the use of the multiple-line syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="1ae5a-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ae5a-146">Example</span></span>  
 <span data-ttu-id="1ae5a-147">L’exemple suivant contient imbriquée `If`... `Then`... `Else` instructions.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-147">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="1ae5a-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ae5a-148">Example</span></span>  
 <span data-ttu-id="1ae5a-149">L’exemple suivant illustre l’utilisation de la syntaxe de ligne simple.</span><span class="sxs-lookup"><span data-stu-id="1ae5a-149">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1ae5a-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ae5a-150">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [<span data-ttu-id="1ae5a-151">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="1ae5a-151">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="1ae5a-152">Select...Case (instruction)</span><span class="sxs-lookup"><span data-stu-id="1ae5a-152">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="1ae5a-153">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="1ae5a-153">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="1ae5a-154">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="1ae5a-154">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="1ae5a-155">Opérateurs logiques et au niveau du bit en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ae5a-155">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="1ae5a-156">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="1ae5a-156">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
