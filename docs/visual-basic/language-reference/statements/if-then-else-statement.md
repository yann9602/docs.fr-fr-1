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
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else, instruction (Visual Basic)
Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="parts"></a>Composants  
 `condition`  
 Obligatoire. Expression. Doit correspondre à `True` ou `False`, ou à un type de données qui est implicitement convertible en `Boolean`.  
  
 Si l’expression est un [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable qui prend la valeur [rien](../../../visual-basic/language-reference/nothing.md), la condition est traitée comme si l’expression n’est pas `True`et le `Else` bloc exécutée.  
  
 `Then`  
 Requis dans la syntaxe de ligne ; facultatif dans la syntaxe de plusieurs lignes.  
  
 `statements`  
 Facultatif. Une ou plusieurs instructions qui suivent `If`... `Then` sont exécutées si `condition` prend la valeur `True`.  
  
 `elseifcondition`  
 Obligatoire si `ElseIf` est présent. Expression. Doit correspondre à `True` ou `False`, ou à un type de données qui est implicitement convertible en `Boolean`.  
  
 `elseifstatements`  
 Facultatif. Une ou plusieurs instructions qui suivent `ElseIf`... `Then` sont exécutées si `elseifcondition` prend la valeur `True`.  
  
 `elsestatements`  
 Facultatif. Une ou plusieurs instructions sont exécutées si aucune `condition` ou `elseifcondition` expression renvoie la valeur `True`.  
  
 `End If`  
 Met fin à la `If`... `Then`... `Else` bloc.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="multiple-line-syntax"></a>Syntaxe sur plusieurs lignes  
 Lorsqu’un `If`... `Then`... `Else` est rencontrée, `condition` est testée. Si `condition` est `True`, les instructions qui suivent `Then` sont exécutées. Si `condition` est `False`, chaque `ElseIf` instruction (le cas échéant) est évaluée dans l’ordre. Lorsqu’un `True``elseifcondition` est trouvée, les instructions qui suit immédiatement la `ElseIf` sont exécutées. Si aucun `elseifcondition` prend la valeur de `True`, ou s’il n’y a aucune `ElseIf` instructions, les instructions qui suivent `Else` sont exécutées. Après l’exécution d’instructions qui suivent `Then`, `ElseIf`, ou `Else`, l’exécution se poursuit avec l’instruction qui suit `End If`.  
  
 Le `ElseIf` et `Else` clauses sont facultatifs. Vous pouvez avoir autant `ElseIf` clauses que vous souhaitez dans un `If`... `Then`... `Else` instruction, mais pas `ElseIf` clause peut apparaître après une `Else` clause. `If`... `Then`... `Else` instructions peuvent être imbriquées dans d’autres.  
  
 Dans la syntaxe de plusieurs lignes, la `If` instruction doit être la seule instruction sur la première ligne. Le `ElseIf`, `Else`, et `End If` instructions peuvent être précédées que par une étiquette de ligne. Le `If`... `Then`... `Else` doit se terminer par un `End If` instruction.  
  
> [!TIP]
>  Le [sélectionnez... Cas d’instruction](../../../visual-basic/language-reference/statements/select-case-statement.md) peuvent être plus utiles lorsque vous évaluez une expression unique qui possède plusieurs valeurs possibles.  
  
## <a name="single-line-syntax"></a>Syntaxe de ligne  
 Vous pouvez utiliser la syntaxe d’une ligne pour les tests courts et simples. Toutefois, la syntaxe de plusieurs lignes offre plus de souplesse et de structure et est généralement plus facile à lire, mettre à jour et le débogage.  
  
 Ce qui suit le `Then` mot clé est examinée pour déterminer si une instruction est une seule ligne `If`. Si l’autre chose qu’un commentaire apparaît après `Then` sur la même ligne, l’instruction est traitée comme une seule ligne `If` instruction. Si `Then` est absent, il doit être le début d’une ligne de plusieurs `If`... `Then`... `Else`.  
  
 Dans la syntaxe de ligne simple, vous pouvez avoir plusieurs instructions exécutées en tant que le résultat d’une `If`... `Then` décision. Toutes les instructions doivent se trouver sur la même ligne et être séparées par un signe deux-points.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la syntaxe de plusieurs lignes de la `If`... `Then`... `Else` instruction.  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient imbriquée `If`... `Then`... `Else` instructions.  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la syntaxe de ligne simple.  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Select...Case (instruction)](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Structures de décision](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Opérateurs logiques et au niveau du bit en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [If (opérateur)](../../../visual-basic/language-reference/operators/if-operator.md)
