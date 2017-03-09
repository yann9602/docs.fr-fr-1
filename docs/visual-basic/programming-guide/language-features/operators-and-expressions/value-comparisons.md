---
title: "Value Comparisons (Visual Basic) | Microsoft Docs"
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
  - "variables [Visual Basic], comparing values"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "comparison operators, comparing expressions"
  - "numeric expressions"
  - "operators [Visual Basic], comparison"
  - "expressions [Visual Basic], comparing"
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Value Comparisons (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez utiliser des opérateurs de comparaison pour construire des expressions qui comparent les valeurs de variables numériques.  Ces expressions retournent une valeur `Boolean` selon que la comparaison est vraie \(true\) ou fausse \(false\).  Des exemples d'une telle expression sont les suivants :  
  
 `45 > 26`  
  
 `26 > 45`  
  
 La première expression prend la valeur `True`, parce que 45 est supérieur à 26.  Le deuxième exemple prend la valeur `False`, parce que 26 n'est pas supérieur à 45.  
  
 Vous pouvez également comparer des expressions numériques de cette façon.  Les expressions comparées peuvent être des expressions complexes, comme dans l'exemple suivant :  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 La précédente expression complexe inclut des littéraux, des variables et des appels de fonction.  Les expressions sont évaluées des deux côtés de l'opérateur de comparaison, et les résultats sont ensuite comparés par l'opérateur de comparaison `>=`.  Si la valeur de l'expression de gauche est supérieure ou égale à la valeur de l'expression de droite, l'expression complète a la valeur `True` ; sinon, elle correspond à `False`.  
  
 Les expressions qui comparent des valeurs sont plus généralement utilisées dans des constructions `If...Then`, comme dans l'exemple suivant :  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/value-comparisons_1.vb)]  
  
 Le signe `=` est un opérateur de comparaison et un opérateur d'assignation.  Lorsque ce signe est utilisé comme un opérateur de comparaison, il évalue si la valeur de gauche est égale à la valeur de droite, comme le montre l'exemple suivant :  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/value-comparisons_2.vb)]  
  
 Vous pouvez également utiliser une expression de comparaison lorsqu'une valeur `Boolean` est requise \(dans une instruction `If`, `While`, `Loop` ou `ElseIf`, par exemple\) ou lors de l'assignation ou du passage d'une valeur à une variable `Boolean`.  Dans l'exemple suivant, la valeur retournée par l'expression de comparaison est assignée à une variable `Boolean` :  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/value-comparisons_3.vb)]  
  
## Voir aussi  
 [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [How to: Calculate Numeric Values](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)