---
title: "/= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb./="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "/= operator [Visual Basic]"
  - "operator /="
  - "compound assignment statements"
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# /= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Divise la valeur d'une variable ou d'une propriété par la valeur d'une expression et assigne le résultat à virgule flottante à cette variable ou propriété.  
  
## Syntaxe  
  
```  
  
variableorproperty /= expression  
```  
  
## Composants  
 `variableorproperty`  
 Obligatoire.  Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire.  Toute expression numérique.  
  
## Notes  
 L'élément situé à gauche de l'opérateur `/=` peut être une simple variable scalaire, une propriété ou un élément d'un tableau.  La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L'opérateur d' `/=` divise d'abord la valeur de la variable ou la propriété \(à gauche de l'opérateur\) par la valeur de l'expression \(situé à droite de l'opérateur\).  L'opérateur assigne le résultat à virgule flottante de cette opération à la variable ou la propriété.  
  
 Cette instruction assigne une valeur d' `Double` à la variable ou la propriété située à gauche.  Si `Option Strict` est `On`, `variableorproperty` doit être un `Double`.  Si `Option Strict` est `Off`, Visual Basic exécute une conversion implicite et assigne la valeur résultante à `variableorproperty`, avec une erreur possible au moment de l'exécution.  Pour plus d'informations, consultez [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## Surcharge  
 L'opérateur [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  La surcharge de l'opérateur `/` affecte le comportement de l'opérateur `/=`.  Si votre code utilise `/=` sur une classe ou structure qui surcharge `/`, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `/=` pour diviser une variable `Integer` par une autre et assigner le quotient à la première variable.  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/floating-point-division-_0_1.vb)]  
  
## Voir aussi  
 [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)   
 [\\\= Operator](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)