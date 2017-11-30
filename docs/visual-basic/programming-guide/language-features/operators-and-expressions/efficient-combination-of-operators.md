---
title: "Association efficace d'opérateurs (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b0f1d637bc1757515cf271a8c70d62effab0843
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-combination-of-operators-visual-basic"></a>Association efficace d'opérateurs (Visual Basic)
Expressions complexes peuvent contenir plusieurs opérateurs distincts. L'exemple suivant illustre ce comportement.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Création d’expressions complexes, tel que celui de l’exemple précédent requiert une connaissance approfondie des règles de priorité des opérateurs. Pour plus d’informations, consultez [priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Expressions entre parenthèses  
 Fréquence à laquelle vous souhaitez opérations dans un ordre différent de celui déterminé par la priorité des opérateurs. Prenons l'exemple suivant.  
  
 `x = z * y + 4`  
  
 L’exemple précédent multiplie `z` par `y`, puis ajoute le résultat à `4`. Mais si vous souhaitez ajouter `y` et `4` avant de multiplier le résultat par `z`, vous pouvez substituer la priorité des opérateurs normale en utilisant des parenthèses. En plaçant une expression entre parenthèses, vous forcez cette expression soit évaluée en premier, quelle que soit la priorité des opérateurs. Pour forcer l’exemple précédent pour effectuer l’ajout de tout d’abord, vous pouvez la réécrire comme dans l’exemple suivant.  
  
 `x = z * (y + 4)`  
  
 L’exemple précédent ajoute `y` et `4`, puis multiplie cette somme par `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Expressions entre parenthèses imbriquées  
 Vous pouvez imbriquer des expressions dans plusieurs niveaux de parenthèses pour substituer davantage la priorité. Les expressions plus profondément imbriquées entre parenthèses sont évaluées en premier, suivie de la prochaine plus profondément imbriquée, et ainsi de suite à la moins profondément imbriquée et enfin les expressions en dehors des parenthèses. L'exemple suivant illustre ce comportement.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 Dans l’exemple précédent, `z + 2` est évaluée en premier, puis les autres expressions entre parenthèses. Élévation à la puissance, qui a généralement la priorité plus élevée que l’addition ou la multiplication, est évaluée en dernier dans cet exemple, car les autres expressions entre parenthèses.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs arithmétiques en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Opérateurs de comparaison en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Opérateurs logiques/de bits (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Expressions booléennes](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Guide pratique : calculer des valeurs numériques](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
