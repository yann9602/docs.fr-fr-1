---
title: "&lt;&lt;= Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.<<="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator <<="
  - "assignment statements, compound"
  - "<<= operator [Visual Basic]"
  - "statements [Visual Basic], compound assignment"
  - "operator<<="
  - "compound assignment statements"
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;&lt;= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Réalise un décalage arithmétique vers la gauche sur la valeur d'une variable ou propriété et assigne le résultat à cette variable ou propriété.  
  
## Syntaxe  
  
```  
  
variableorproperty <<= amount  
```  
  
## Composants  
 `variableorproperty`  
 Obligatoire.  Variable ou propriété d'un type intégral \(`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`\).  
  
 `amount`  
 Obligatoire.  Expression numérique d'un type de données qui s'étend à `Integer`.  
  
## Notes  
 L'élément situé à gauche de l'opérateur `<<=` peut être une simple variable scalaire, une propriété ou un élément d'un tableau.  La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L'opérateur d' `<<=` exécute d'abord un décalage arithmétique vers la gauche sur la valeur de la variable ou la propriété.  L'opérateur assigne le résultat de cette opération vers cette variable ou une propriété.  
  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés à une extrémité du résultat ne sont pas réintroduits à l'autre extrémité.  Dans un décalage arithmétique vers la gauche, les bits décalés au\-delà de la plage du type de données de résultat sont ignorés, et les positions des bits libérées à droite ont la valeur zéro.  
  
## Surcharge  
 [\<\< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) peut être *surchargé*, ce qui signifie qu'une classe ou structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou structure.  La surcharge de l'opérateur `<<` affecte le comportement de l'opérateur `<<=`.  Si votre code utilise `<<=` sur une classe ou structure qui surcharge `<<`, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `<<=` pour décaler le modèle binaire d'une variable `Integer` vers la gauche selon les valeurs spécifiées et assigner le résultat à cette variable.  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## Voir aussi  
 [\<\< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)