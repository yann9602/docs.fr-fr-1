---
title: "Boolean Expressions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "short-circuiting"
  - "Boolean expressions"
  - "logical operators, Boolean expressions"
  - "expressions [Visual Basic], Boolean"
  - "expression evaluation, Boolean expressions"
  - "operators [Visual Basic], short-circuiting"
  - "Visual Basic code, operators"
  - "short-circuit evaluation"
  - "logical operators, short-circuiting"
  - "operators [Visual Basic], Boolean"
  - "Visual Basic code, expressions"
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Boolean Expressions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une *expression booléenne* correspond à une valeur du [type de données booléen](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) : `True` ou `False`.  Les expressions `Boolean` peuvent se présenter sous plusieurs formes.  La forme la plus simple est la comparaison directe de la valeur d'une variable `Boolean` à un littéral `Boolean`, comme le montre l'exemple suivant :  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## Deux significations de l'opérateur \=  
 Notez que l'instruction d'assignation `newCustomer = True` ressemble à l'expression de l'exemple précédent, mais elle effectue une fonction différente et est utilisée différemment.  Dans l'exemple précédent, l'expression `newCustomer = True` représente une valeur Boolean et le signe `=` est interprété comme un opérateur de comparaison.  Dans une instruction autonome, le signe `=` est interprété comme un opérateur d'assignation et assigne la valeur de droite à la variable de gauche.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 Pour plus d'informations, consultez [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) et [Statements](../../../../visual-basic/language-reference/statements/index.md).  
  
## Opérateurs de comparaison  
 Les opérateurs de comparaison \(`=`, `<`, `>`, `<>`, `<=` et `>=`\) produisent des expressions booléennes en comparant l'expression située à gauche de l'opérateur à l'expression de droite et en assignant la valeur `True` ou `False` au résultat.  L'exemple suivant illustre ce comportement.  
  
 `42 < 81`  
  
 Étant donné que 42 est inférieur à 81, l'expression booléenne de l'exemple précédent a la valeur `True`.  Pour plus d'informations sur ce type d'expression, consultez [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### Opérateurs de comparaison associés aux opérateurs logiques  
 Les expressions de comparaison peuvent être combinées à l'aide d'opérateurs logiques pour créer des expressions booléennes plus complexes.  L'exemple suivant illustre l'utilisation d'opérateurs de comparaison associés à un opérateur logique.  
  
 `x > y And x < 1000`  
  
 Dans cet exemple, la valeur de l'expression globale dépend des valeurs des expressions de chaque côté de l'opérateur `And`.  Si les deux expressions ont la valeur `True`, l'expression globale a la valeur `True`.  Si l'une des expressions a la valeur `False`, l'expression globale a la valeur `False`.  
  
## Opérateurs de court\-circuit  
 Les opérateurs logiques `AndAlso` et `OrElse` se comportent comme des *courts\-circuits*.  Un opérateur de court\-circuit évalue premièrement l'opérande de gauche.  Si l'opérande de gauche détermine la valeur de l'expression globale, l'exécution du programme se poursuit sans évaluer l'expression de droite.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 Dans l'exemple précédent, l'opérateur évalue l'expression de gauche, `45 < 12`.  Puisque l'expression de gauche a pour valeur `False`, l'expression logique globale doit avoir la valeur `False`.  L'exécution du programme ignore ainsi l'exécution du code dans le bloc `If` sans évaluer l'expression de droite, `testFunction(3)`.  Cet exemple n'appelle pas `testFunction()` parce que l'expression de gauche falsifie l'expression globale.  
  
 De même, si l'expression de gauche d'une expression logique utilisant `OrElse` a la valeur `True`, l'exécution se poursuit sur la prochaine ligne de code sans évaluer l'expression de droite, car l'expression de gauche a déjà validé l'expression complète.  
  
### Comparaison avec des opérateurs n'effectuant pas de court\-circuit  
 En revanche, les deux côtés de l'opérateur logique sont évalués lors de l'utilisation des opérateurs logiques `And` et `Or`.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 L'exemple précédent appelle `testFunction()` même si l'expression de gauche a la valeur `False`.  
  
## Expressions entre parenthèses  
 Vous pouvez utiliser des parenthèses pour contrôler l'ordre d'évaluation des expressions booléennes.  Les expressions entre parenthèses sont évaluées en premier lieu.  Pour plusieurs niveaux d'imbrication, la priorité est accordée aux expressions les plus profondément imbriquées.  Au sein des parenthèses, l'évaluation se poursuit selon les règles de priorité des opérateurs.  Pour plus d'informations, consultez [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## Voir aussi  
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Statements](../../../../visual-basic/programming-guide/language-features/statements.md)   
 [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)