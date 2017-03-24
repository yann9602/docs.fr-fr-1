---
title: "If...Then...Else Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ElseIf"
  - "vb.Then"
  - "vb.If"
  - "vb.EndIf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ElseIf statement, If...Then...Else"
  - "Then statement, If...Then...Else"
  - "control flow, branching"
  - "execution, conditional"
  - "TypeOf...Is expression, and If...Then...Else statements"
  - "If...Then...Else statements"
  - "If statement, If...Then...Else"
  - "If statement"
  - "Is operator [Visual Basic], in If...Then...Else statements"
  - "If Operator [Visual Basic]"
  - "branching, conditional"
  - "IIf function, and If...Then...Else statements"
  - "Else statement [Visual Basic]"
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# If...Then...Else Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.  
  
## Syntaxe  
  
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
  
## Composants  
 `condition`  
 Requis.  Expression.  Doit avoir pour valeur `True` ou `False`, ou un type de données implicitement convertible en `Boolean`.  
  
 Si l'expression est une variable de [nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` qui correspond à [rien](../../../visual-basic/language-reference/nothing.md), la condition est traitée comme si l'expression n'est pas `True`, et le bloc d' `Else` est exécuté.  
  
 `Then`  
 Obligatoire dans la syntaxe à une seule ligne, facultatif dans la syntaxe multiligne.  
  
 `statements`  
 Optionnel.  Une ou plusieurs instructions qui suivent `If`...`Then` sont exécutées si `condition` a la valeur `True`.  
  
 `elseifcondition`  
 Obligatoire si `ElseIf` is présent.  Expression.  Doit avoir pour valeur `True` ou `False`, ou un type de données implicitement convertible en `Boolean`.  
  
 `elseifstatements`  
 Optionnel.  Une ou plusieurs instructions qui suivent `ElseIf`...`Then` sont exécutées si `elseifcondition` a la valeur `True`.  
  
 `elsestatements`  
 Optionnel.  Une ou plusieurs instructions sont exécutées si aucune expression `condition` ou `elseifcondition` précédente n'a la valeur `True`.  
  
 `End If`  
 Met fin au bloc `If`...`Then`...`Else`.  
  
## Notes  
  
## Syntaxe sur plusieurs lignes  
 Lorsqu'une instruction `If`...`Then`...`Else` est rencontrée, `condition` est testée.  Si `condition` a la valeur `True`, les instructions qui suivent `Then` sont exécutées.  Si `condition` a la valeur `False`, chaque instruction `ElseIf` \(le cas échéant\) est évaluée à tour de rôle.  Quand une `elseifcondition` de valeur `True` est trouvée, les instructions qui suivent immédiatement l'instruction `ElseIf` correspondante sont exécutées.  Si aucune `elseifcondition` n'a la valeur `True`, ou s'il n'existe aucune instruction `ElseIf`, les instructions qui suivent `Else` sont exécutées.  Après l'exécution des instructions qui suivent `Then`, `ElseIf` ou `Else`, l'exécution se poursuit avec l'instruction qui suit `End If`.  
  
 Les clauses `ElseIf` et `Else` sont toutes deux facultatives.  Vous pouvez avoir autant de clauses `ElseIf` que vous le souhaitez dans une instruction `If`...`Then`...`Else`, mais aucune clause `ElseIf` ne peut apparaître après une clause `Else`.  Les instructions `If`...`Then`...`Else` peuvent être imbriquées à l'intérieur les unes des autres.  
  
 Dans la syntaxe multiligne, l'instruction `If` doit être la seule instruction présente sur la première ligne.  Les instructions `ElseIf`, `Else` et `End If` ne peuvent être précédées que par une étiquette de ligne.  Le bloc `If`...`Then`...`Else` doit se terminer par une instruction `End If`.  
  
> [!TIP]
>  [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) peut s'avérer mieux adapté à l'évaluation d'une seule expression qui possède plusieurs valeurs possibles.  
  
## Syntaxe à une seule ligne  
 Vous pouvez utiliser la syntaxe à une seule ligne pour effectuer de petits tests simples.  Toutefois, la syntaxe multiligne fournit une plus grande structure et davantage de souplesse. En outre, elle est généralement plus facile à lire, à gérer et à déboguer.  
  
 Ce qui suit le mot clé `Then` est examiné pour déterminer si une instruction correspond à `If` sur une seule ligne.  Si tout élément autre qu'un commentaire apparaît après `Then` sur la même ligne, l'instruction est traitée comme une instruction `If` à une seule ligne.  Si `Then` est absent, il s'agit du début d'une instruction `If`...`Then`...`Else` multiligne.  
  
 Dans la syntaxe à une seule ligne, plusieurs instructions peuvent être exécutées à la suite d'une décision `If`...`Then`.  Toutes les instructions doivent être présentes sur la même ligne et être séparées par le signe deux\-points.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la syntaxe sur plusieurs lignes de l'instruction `If`...`Then`...`Else`.  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## Exemple  
 L'exemple suivant contient des instructions `If`...`Then`...`Else` imbriquées.  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la syntaxe à une seule ligne.  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Decision Structures](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)