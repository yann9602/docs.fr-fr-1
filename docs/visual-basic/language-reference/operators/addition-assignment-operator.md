---
title: "+= Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.+="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "+= operator [Visual Basic]"
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "+= operator [Visual Basic], appending strings"
  - "compound assignment statements"
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# += Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ajoute la valeur d'une expression numérique à la valeur d'une variable ou propriété numérique et assigne le résultat à la variable ou propriété.  Peut également être utilisé pour concaténer une expression `String` à une variable ou une propriété `String` et assigner le résultat à la variable ou propriété.  
  
## Syntaxe  
  
```  
  
variableorproperty += expression  
```  
  
## Composants  
 `variableorproperty`  
 Obligatoire.  Toute variable ou propriété numérique ou `String`.  
  
 `expression`  
 Obligatoire.  Toute expression numérique ou `String`.  
  
## Notes  
 L'élément situé à gauche de l'opérateur `+=` peut être une simple variable scalaire, une propriété ou un élément d'un tableau.  La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L'opérateur d' `+=` ajoute la valeur sur sa droite à la variable ou la propriété dans sa gauche, et assigne le résultat à la variable ou la propriété dans sa gauche.  L'opérateur d' `+=` peut également être utilisé pour concaténer l'expression d' `String` sur sa droite à la variable d' `String` ou la propriété dans sa gauche, et assigne le résultat à la variable ou la propriété dans sa gauche.  
  
> [!NOTE]
>  Si vous utilisez l'opérateur `+=`, il vous sera parfois difficile de déterminer si une addition ou une concaténation de chaînes se produira.  Utilisez l'opérateur `&=` pour la concaténation afin d'éliminer toute ambiguïté et de fournir un code auto\-documenté.  
  
 Cet opérateur d'assignation effectue implicitement des conversions étendues, mais pas restrictives, si l'environnement de compilation applique des sémantiques strictes.  Pour plus d'informations sur ces conversions, consultez [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  Pour plus d'informations sur les sémantiques strictes et permissives, consultez [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Si les sémantiques permissives sont autorisées, l'opérateur `+=` exécute implicitement un ensemble de conversions de chaînes et de conversions numériques identiques à celles exécutées par l'opérateur `+`.  Pour plus d'informations sur ces conversions, consultez [\+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## Surcharge  
 L'opérateur `+` peut être *surchargé*, ce qui signifie qu'une classe ou structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou structure.  La surcharge de l'opérateur `+` affecte le comportement de l'opérateur `+=`.  Si votre code utilise `+=` sur une classe ou structure qui surcharge `+`, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `+=` pour combiner la valeur d'une variable à une autre.  La première partie utilise `+=` avec des variables numériques pour ajouter une valeur à une autre.  La seconde partie utilise `+=` avec des variables `String` pour concaténer une valeur à une autre.  Dans les deux cas, le résultat est assigné à la première variable.  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 La valeur de `num1` est maintenant 13 et la valeur de `str1` est maintenant "103".  
  
## Voir aussi  
 [\+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)