---
title: "Operators and Expressions in Visual Basic | Microsoft Docs"
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
  - "operators [Visual Basic], operands"
  - "operators [Visual Basic]"
  - "operands, definition"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "operands"
  - "expressions [Visual Basic]"
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Operators and Expressions in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Un *opérateur* est un élément de code qui exécute une opération sur un ou plusieurs éléments de code qui contiennent des valeurs.  Les éléments de valeur comprennent des variables, des constantes, des littéraux, des propriétés, des retours provenant des procédures `Function` et `Operator` et des expressions.  
  
 Une *expression* est une série d'éléments de valeur associés aux opérateurs, ce qui retourne une nouvelle valeur.  Les opérateurs agissent sur les éléments de valeur en effectuant des calculs, des comparaisons et d'autres opérations.  
  
## Types d'opérateurs  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] fournit les types d'opérateurs suivants :  
  
-   Les [opérateurs arithmétiques](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) qui exécutent des calculs familiers sur les valeurs numériques, y compris le décalage de leurs modèles binaires.  
  
-   Les [opérateurs de comparaison](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) qui comparent deux expressions et retournent une valeur `Boolean` représentant le résultat de la comparaison.  
  
-   Les [opérateurs de concaténation](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) qui relient plusieurs chaînes dans une seule chaîne.  
  
-   Les [opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) qui combinent des valeurs `Boolean` ou numériques et retournent un résultat du même type de données que les valeurs.  
  
 Les éléments de valeur associés à un opérateur sont appelés *opérandes* de cet opérateur.  Les opérateurs associés aux éléments de valeur forment des expressions, à l'exception de l'opérateur d'assignation qui forme une *instruction*.  Pour plus d'informations, consultez [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## Évaluation des expressions  
 Le résultat final d'une expression représente une valeur qui fait partie généralement d'un type de données familier tel que `Boolean`, `String` ou d'un type numérique.  
  
 Voici des exemples d'expressions.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Plusieurs opérateurs peuvent effectuer des actions dans une expression ou une instruction unique, comme le montrent les exemples ci\-dessous.  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 Dans l'exemple précédent, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] exécute les opérations de l'expression à droite de l'opérateur d'assignation \(`=`\), puis assigne la valeur du résultat à la variable `x` située à gauche.  Le nombre d'opérateurs pouvant être combinés dans une expression est illimité, mais la connaissance de [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) est nécessaire pour garantir que vous obtiendrez les résultats escomptés.  
  
 Pour plus d'informations et d'exemples, consultez la page [Surcharge d'opérateur dans Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703) \(en anglais\).  
  
## Voir aussi  
 [Operators](../../../../visual-basic/language-reference/operators/index.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)