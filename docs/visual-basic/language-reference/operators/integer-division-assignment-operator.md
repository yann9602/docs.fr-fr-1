---
title: "-= Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.-="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-= operator [Visual Basic]"
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "operator -="
  - "compound assignment statements"
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# -= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Soustrait la valeur d'une expression de la valeur d'une variable ou d'une propriété et assigne le résultat à la variable ou à la propriété.  
  
## Syntaxe  
  
```  
  
variableorproperty -= expression  
```  
  
## Composants  
 `variableorproperty`  
 Obligatoire.  Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire.  Toute expression numérique.  
  
## Notes  
 L'élément situé à gauche de l'opérateur `-=` peut être une simple variable scalaire, une propriété ou un élément d'un tableau.  La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L'opérateur d' `-=` soustrait d'abord la valeur de l'expression \(situé à droite de l'opérateur\) de la valeur de la variable ou la propriété \(à gauche de l'opérateur\).  L'opérateur assigne le résultat de cette opération à la variable ou la propriété.  
  
## Surcharge  
 [\- Operator](../../../visual-basic/language-reference/operators/subtraction-operator.md) peut être *surchargé*, ce qui signifie qu'une classe ou structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou structure.  La surcharge de l'opérateur `-` affecte le comportement de l'opérateur `-=`.  Si votre code utilise `-=` sur une classe ou structure qui surcharge `-`, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `-=` pour soustraire une variable `Integer` d'une autre et assigner le résultat à la dernière variable.  
  
 [!code-vb[VbVbalrOperators#11](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## Voir aussi  
 [\- Operator](../../../visual-basic/language-reference/operators/subtraction-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)