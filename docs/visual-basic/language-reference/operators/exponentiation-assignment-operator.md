---
title: "^= Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.^="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "^= operator [Visual Basic]"
  - "compound assignment statements"
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ^= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Élève la valeur d'une variable ou d'une propriété à la puissance d'une expression et assigne le résultat à cette variable ou propriété.  
  
## Syntaxe  
  
```  
  
variableorproperty ^= expression  
```  
  
## Composants  
 `variableorproperty`  
 Obligatoire.  Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire.  Toute expression numérique.  
  
## Notes  
 L'élément situé à gauche de l'opérateur `^=` peut être une simple variable scalaire, une propriété ou un élément d'un tableau.  La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L'opérateur d' `^=` déclenche d'abord la valeur de la variable ou la propriété \(à gauche de l'opérateur\) à la puissance de la valeur de l'expression \(situé à droite de l'opérateur\).  L'opérateur assigne le résultat de cette opération dans la variable ou la propriété.  
  
 Visual Basic exécute toujours l'élévation à la puissance dans le [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).  Les opérandes de tous les types différents sont converties en `Double` et le résultat est toujours `Double`.  
  
 La valeur de `expression` peut être fractionnaire, négative ou les deux.  
  
## Surcharge  
 L'opérateur [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  La surcharge de l'opérateur `^` affecte le comportement de l'opérateur `^=`.  Si votre code utilise `^=` sur une classe ou structure qui surcharge `^`, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `^=` pour élever la valeur d'une variable `Integer` à la puissance d'une seconde variable et assigner le résultat à la première variable.  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## Voir aussi  
 [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)