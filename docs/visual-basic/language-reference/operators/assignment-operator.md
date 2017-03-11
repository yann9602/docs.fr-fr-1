---
title: "= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Assign"
  - "vb.="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "= operator [Visual Basic]"
  - "= assignment statements [Visual Basic]"
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# = Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Assigne une valeur à une variable ou une propriété.  
  
## Syntaxe  
  
```  
  
variableorproperty = value  
```  
  
## Composants  
 `variableorproperty`  
 Toute variable ou toute propriété accessible en écriture.  
  
 `value`  
 Tout littéral, constante ou expression.  
  
## Notes  
 L'élément situé à gauche du signe égal \(`=`\) peut être une simple variable scalaire, une propriété ou un élément d'un tableau.  La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  L'opérateur `=` assigne la valeur du côté droit à la variable ou à la propriété du côté gauche.  
  
> [!NOTE]
>  L'opérateur `=` est également utilisé comme un opérateur de comparaison.  Pour plus d'informations, consultez [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## Surcharge  
 L'opérateur `=` peut être surchargé uniquement en tant qu'opérateur de comparaison relationnel et non comme un opérateur d'assignation.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant illustre l'opérateur d'assignation.  La valeur située à droite est assignée à la variable située à gauche.  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/assignment-operator_1.vb)]  
  
## Voir aussi  
 [&\= Operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [\*\= Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [\+\= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)   
 [\-\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\\\= Operator](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [^\= Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)