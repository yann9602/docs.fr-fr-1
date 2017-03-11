---
title: "How to: Calculate Numeric Values (Visual Basic) | Microsoft Docs"
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
  - "operator precedence"
  - "operators [Visual Basic]"
  - "expressions [Visual Basic], numeric"
  - "calculations, numeric expressions"
  - "precedence, of operators"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "numeric expressions"
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Calculate Numeric Values (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez calculer des valeurs numériques à l'aide d'expressions numériques.  Une *expression numérique* contient des littéraux, des constantes et des variables représentant des valeurs numériques, ainsi que des opérateurs qui agissent sur ces valeurs.  
  
## Calcul de valeurs numériques  
  
#### Pour calculer une valeur numérique  
  
-   Combinez un ou plusieurs littéraux, constantes et variables numériques dans une expression numérique.  Vous trouverez ci\-dessous des exemples d'expressions numériques valides.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     Les trois premières lignes affichent un littéral, une constante et une variable.  Chacune d'elle forme une expression numérique valide par elle\-même.  La dernière ligne affiche une combinaison d'une variable avec deux littéraux.  
  
     Notez qu'une expression numérique ne constitue pas une instruction [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] complète par elle\-même.  Vous devez utiliser l'expression dans le cadre d'une instruction complète.  
  
#### Pour stocker une valeur numérique  
  
-   Vous pouvez utiliser une instruction d'assignation pour assigner la valeur représentée par une expression numérique à une autre variable, comme illustré dans cet exemple.  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-calculate-numeric_1.vb)]  
  
     Dans l'exemple précédent, la valeur de l'expression située à droite de l'opérateur égal \(`=`\) \(equals\) est assignée à la variable `j` située à gauche de l'opérateur ; par conséquent, `j` a la valeur 276.  
  
     Pour plus d'informations, consultez [Statements](../../../../visual-basic/language-reference/statements/index.md).  
  
## Opérateurs multiples  
 Si l'expression numérique contient plusieurs opérateurs, ceux\-ci sont évalués en fonction de l'ordre déterminé par les règles de priorité des opérateurs.  Pour substituer ces règles de priorité d'opérateurs, vous devez insérer des parenthèses autour des expressions, comme le montre l'exemple précédent ; les expressions insérées sont évaluées en premier lieu.  
  
#### Pour substituer la priorité d'opérateurs normale  
  
-   Utilisez des parenthèses pour insérer les opérations à effectuer en premier lieu.  L'exemple suivant affiche deux résultats différents avec les mêmes opérandes et opérateurs.  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-calculate-numeric_2.vb)]  
  
     Dans l'exemple précédent, le calcul de `j` exécute d'abord l'opérateur d'addition \(`+`\) parce que les parenthèses qui entourent `(67 + i)` substituent la priorité normale et la valeur assignée à `j` est de 276 \(4 fois 69\).  Le calcul de `k` exécute les opérateurs dans leur priorité normale \(`*` avant `+`\) et la valeur assignée à `k` est de 270 \(268 plus 2\).  
  
     Pour plus d'informations, consultez [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## Voir aussi  
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)