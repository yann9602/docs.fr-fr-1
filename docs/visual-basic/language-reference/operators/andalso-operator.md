---
title: "AndAlso Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AndAlso"
  - "AndAlso"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "short-circuiting"
  - "AndAlso operator"
  - "operators [Visual Basic], short-circuiting"
  - "operators [Visual Basic], conjunction"
  - "short-circuit evaluation"
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# AndAlso Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Effectue une conjonction logique "court\-circuitante" sur deux expressions.  
  
## Syntaxe  
  
```  
  
result = expression1 AndAlso expression2  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`result`|Obligatoire.  Toute expression `Boolean`.  Le résultat est le résultat `Boolean` de la comparaison des deux expressions.|  
|`expression1`|Obligatoire.  Toute expression `Boolean`.|  
|`expression2`|Obligatoire.  Toute expression `Boolean`.|  
  
## Notes  
 Une opération logique est dite *court\-circuitante* si le code compilé peut ignorer l'évaluation d'une expression en fonction du résultat d'une autre expression.  Si le résultat de la première expression évaluée détermine le résultat final de l'opération, il n'y a pas besoin d'évaluer l'autre expression, car elle ne peut pas changer le résultat final.  Un court circuit peut améliorer les performances si l'expression ignorée est complexe ou si elle implique des appels de procédure.  
  
 Si les deux expressions ont la valeur `True`, `result` est `True`.  Le tableau suivant illustre la manière dont `result` est déterminé.  
  
||||  
|-|-|-|  
|Si `expression1` est :|Et `expression2` a la valeur|La valeur de `result` est|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|\(non évaluée\)|`False`|  
  
## Types de données  
 L'opérateur `AndAlso` est défini uniquement pour [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).  Visual Basic convertit chaque opérande si nécessaire en `Boolean` et exécute l'opération entière en `Boolean`.  Si vous assignez le résultat à un type numérique, Visual Basic le convertit de `Boolean` en ce type.  Cette conversion pourrait avoir comme conséquence un comportement inattendu.  Par exemple, `5 AndAlso 12` donne `–1` lorsqu'il est converti en `Integer`.  
  
## Surcharge  
 [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) et [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) peuvent être *surchargés*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  La surcharge des opérateurs `And` et `IsFalse` affecte le comportement de l'opérateur `AndAlso`.  Si votre code utilise `AndAlso` sur une classe ou une structure qui surcharge `And` et `IsFalse`, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `AndAlso` pour effectuer une conjonction logique sur deux expressions.  Le résultat est une valeur `Boolean` qui indique si l'expression conjointe entière est true.  Si la première expression est `False`, la seconde n'est pas évaluée.  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/andalso-operator_1.vb)]  
  
 L'exemple précédent produit respectivement les résultats suivants : `True`, `False` et `False`.  Dans le calcul de `secondCheck`, la seconde expression n'est pas évaluée parce que la première a déjà la valeur `False`.  Toutefois, la seconde expression est évaluée dans le calcul de `thirdCheck`.  
  
## Exemple  
 L'exemple suivant montre une procédure `Function` qui recherche une valeur donnée parmi les éléments d'un tableau.  Si le tableau est vide ou si la longueur de tableau a été dépassée, l'instruction `While` ne teste pas l'élément de tableau pour la valeur de recherche.  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/andalso-operator_2.vb)]  
  
## Voir aussi  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [And Operator](../../../visual-basic/language-reference/operators/and-operator.md)   
 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)