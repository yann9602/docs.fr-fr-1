---
title: "OrElse Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "OrElse"
  - "vb.OrElse"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "short-circuiting"
  - "operators [Visual Basic], short-circuiting"
  - "operators [Visual Basic], disjunction"
  - "short-circuit evaluation"
  - "OrElse operator [Visual Basic]"
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# OrElse Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Effectue une disjonction logique inclusive "court\-circuitante" sur deux expressions.  
  
## Syntaxe  
  
```  
  
result = expression1 OrElse expression2  
```  
  
## Composants  
 `result`  
 Obligatoire.  Toute expression `Boolean`.  
  
 `expression1`  
 Obligatoire.  Toute expression `Boolean`.  
  
 `expression2`  
 Obligatoire.  Toute expression `Boolean`.  
  
## Notes  
 Une opération logique est dite *court\-circuitante* si le code compilé peut ignorer l'évaluation d'une expression en fonction du résultat d'une autre expression.  Si le résultat de la première expression évaluée détermine le résultat final de l'opération, il n'y a pas besoin d'évaluer l'autre expression, car elle ne peut pas changer le résultat final.  Un court circuit peut améliorer les performances si l'expression ignorée est complexe ou si elle implique des appels de procédure.  
  
 Si une ou les deux expressions ont la valeur `True`, `result` a la valeur `True`.  Le tableau suivant illustre la manière dont `result` est déterminé.  
  
|Si `expression1` est :|Et `expression2` a la valeur|La valeur de `result` est|  
|----------------------------|----------------------------------|-------------------------------|  
|`True`|\(non évaluée\)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## Types de données  
 L'opérateur `OrElse` est défini uniquement pour [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).  Visual Basic convertit chaque opérande si nécessaire en `Boolean` et exécute l'opération entière en `Boolean`.  Si vous assignez le résultat à un type numérique, Visual Basic le convertit de `Boolean` en ce type.  Cette conversion pourrait avoir comme conséquence un comportement inattendu.  Par exemple, `5 OrElse 12` donne `–1` lorsqu'il est converti en `Integer`.  
  
## Surcharge  
 [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) et [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) peuvent être *surchargés*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  La surcharge des opérateurs `Or` et `IsTrue` affecte le comportement de l'opérateur `OrElse`.  Si votre code utilise `OrElse` sur une classe ou une structure qui surcharge `Or` et `IsTrue`, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `OrElse` pour effectuer une disjonction logique sur deux expressions.  Le résultat est une valeur `Boolean` qui indique si l'une des deux expressions est true.  Si la première expression est `True`, la seconde n'est pas évaluée.  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/orelse-operator_1.vb)]  
  
 L'exemple précédent produit respectivement les résultats suivants : `True`, `True` et `False`.  Dans le calcul de `firstCheck`, la seconde expression n'est pas évaluée parce que la première a déjà la valeur `True`.  Toutefois, la seconde expression est évaluée dans le calcul de `secondCheck`.  
  
## Exemple  
 L'exemple suivant affiche une instruction `If`...`Then` qui contient deux appels de procédure.  Si le premier appel retourne `True`, la seconde procédure n'est pas appelée.  Si la seconde procédure effectue des tâches importantes qui doivent toujours être effectuées lorsque cette section de code est exécutée, des résultats inattendus pourraient se produire.  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/orelse-operator_2.vb)]  
  
## Voir aussi  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md)   
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)