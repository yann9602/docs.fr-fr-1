---
title: "\= Operator | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "\="
  - "vb.\="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "\= operator [Visual Basic]"
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "operator \= [Visual Basic]"
  - "compound assignment statements"
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# \= Operator
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Divise la valeur d'une variable ou d'une propriété par la valeur d'une expression et assigne le résultat sous forme d'entier à cette variable ou propriété.  
  
## Syntaxe  
  
```  
  
variableorproperty \= expression  
```  
  
## Composants  
 `variableorproperty`  
 Obligatoire.  Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire.  Toute expression numérique.  
  
## Notes  
 L'élément situé à gauche de l'opérateur `\=` peut être une simple variable scalaire, une propriété ou un élément d'un tableau.  La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L'opérateur d' `\=` divise la valeur d'une variable ou d'une propriété sur la gauche par la valeur sur sa droite, et assigne le résultat entier à la variable ou la propriété dans sa gauche  
  
 Pour plus d'informations sur la division par un entier, consultez [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md).  
  
## Surcharge  
 L'opérateur `\` peut être *surchargé*, ce qui signifie qu'une classe ou structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou structure.  La surcharge de l'opérateur `\` affecte le comportement de l'opérateur `\=`.  Si votre code utilise `\=` sur une classe ou structure qui surcharge `\`, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `\=` pour diviser une variable `Integer` par une autre et assigner le résultat sous forme d'entier à la première variable.  
  
 [!code-vb[VbVbalrOperators#19](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/subtraction-assignment-o_2_1.vb)]  
  
## Voir aussi  
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)