---
title: "Efficient Combination of Operators (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "expressions [Visual Basic], parentheses"
  - "operators [Visual Basic], associativity"
  - "expressions [Visual Basic], operators"
  - "operators [Visual Basic], precedence"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "operators [Visual Basic], complex expressions"
  - "expressions [Visual Basic], complex"
  - "parentheses, complex expressions"
  - "numeric expressions"
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Efficient Combination of Operators (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Des expressions complexes peuvent contenir plusieurs opérateurs distincts.  L'exemple suivant illustre ce comportement.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 La création d'expressions complexes comme celle de l'exemple précédent nécessite de bien connaître les règles de priorité des opérateurs.  Pour plus d'informations, consultez [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## Expressions entre parenthèses  
 Vous voulez parfois que les opérations soient effectuées dans un ordre différent de celui déterminé par la priorité des opérateurs.  Prenons l'exemple suivant.  
  
 `x = z * y + 4`  
  
 L'exemple précédent multiplie `z` par `y`, puis ajoute le résultat à `4`.  Mais si vous souhaitez ajouter `y` et `4` avant de multiplier le résultat par `z`, vous pouvez substituer la priorité des opérateurs normale en utilisant des parenthèses.  En effet, si vous insérez des parenthèses autour d'une expression, cette expression sera d'abord évaluée, sans tenir compte de la priorité des opérateurs.  Pour forcer l'exemple précédent à effectuer l'addition en premier lieu, vous pouvez le réécrire comme dans l'exemple suivant.  
  
 `x = z * (y + 4)`  
  
 L'exemple précédent ajoute `y` et `4`, puis multiplie cette somme par `z`.  
  
### Expressions entre parenthèses imbriquées  
 Vous pouvez imbriquer les expressions dans plusieurs niveaux de parenthèses pour substituer davantage la priorité.  Les expressions les plus imbriquées dans les parenthèses sont évaluées en premier lieu, suivies des expressions suivantes les plus imbriquées, etc. jusqu'à celles les moins imbriquées et, enfin, des expressions à l'extérieur des parenthèses.  L'exemple suivant illustre ce comportement.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 Dans l'exemple précédent, `z + 2` est évalué en premier lieu, suivi des autres expressions entre parenthèses.  L'élévation à la puissance, qui est en principe prioritaire par rapport à l'addition ou à la multiplication, est évaluée en dernier lieu dans cet exemple, car les autres expressions figurent entre parenthèses.  
  
## Voir aussi  
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Logical\/Bitwise Operators](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [How to: Calculate Numeric Values](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)