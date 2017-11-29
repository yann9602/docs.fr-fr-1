---
title: Comparaisons de valeurs (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c11f12bbaf261c0853e96802f03322c5e7fdc706
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="value-comparisons-visual-basic"></a>Comparaisons de valeurs (Visual Basic)
Opérateurs de comparaison peuvent être utilisés pour construire des expressions qui comparent les valeurs des variables numériques. Ces expressions retournent un `Boolean` valeur selon que la comparaison est true ou false. Voici quelques exemples d’une telle expression.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 La première expression prend la valeur `True`, car 45 est supérieur à 26. Le deuxième exemple prend la valeur `False`, car 26 n’est pas supérieur à 45.  
  
 Vous pouvez également comparer des expressions numériques de cette façon. Vous comparez des expressions peuvent être des expressions complexes, comme dans l’exemple suivant.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 La précédente expression complexe inclut des littéraux, des variables et des appels de fonction. Les expressions des deux côtés de l’opérateur de comparaison sont évaluées et les valeurs résultantes sont ensuite comparés à l’aide de la `>=` opérateur de comparaison. Si la valeur de l’expression de gauche est supérieure ou égale à la valeur de l’expression de droite, toute l’expression prend la valeur de `True`; sinon, elle prend la valeur `False`.  
  
 Les expressions qui comparent des valeurs sont couramment utilisées dans `If...Then` constructions, comme dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 Le `=` signe est un opérateur de comparaison et un opérateur d’assignation. Lorsqu’il est utilisé comme opérateur de comparaison, il évalue si la valeur de gauche est égale à la valeur à droite, comme indiqué dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 Vous pouvez également utiliser une expression de comparaison n’importe où un `Boolean` valeur est nécessaire, comme dans un `If`, `While`, `Loop`, ou `ElseIf` instruction, ou lors de l’assignation ou du passage d’une valeur à une `Boolean` variable. Dans l’exemple suivant, la valeur retournée par l’expression de comparaison est affectée à un `Boolean` variable.  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions booléennes](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Opérateurs et expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Opérateurs de comparaison en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Guide pratique : calculer des valeurs numériques](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
