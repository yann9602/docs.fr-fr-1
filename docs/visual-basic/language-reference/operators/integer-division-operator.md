---
title: "\ Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.\"
  - "\"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "division operator, integer"
  - "integer division operator"
  - "zero, division by zero"
  - "arithmetic operators, division"
  - "division, by zero"
  - "backslash (\) [Visual Basic]"
  - "\ operator [Visual Basic]"
  - "integer quotient"
  - "math operators"
  - "quotients, integer"
  - "truncation, integer division"
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# \ Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Effectue la division de deux nombres et retourne le résultat sous forme d'entier.  
  
## Syntaxe  
  
```  
  
expression1 \ expression2  
```  
  
## Composants  
 `expression1`  
 Obligatoire.  Toute expression numérique.  
  
 `expression2`  
 Obligatoire.  Toute expression numérique.  
  
## Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante, ainsi que `Decimal`.  
  
## Résultat  
 Le résultat est le quotient entier de `expression1` divisé par `expression2` qui abandonne tout reste et conserve uniquement la partie entière.  Ce concept porte le nom de *troncation*.  
  
 Le type de données de résultat est un type numérique approprié aux types de données de `expression1` et `expression2`.  Consultez les tableaux « Arithmétique sur les entiers » dans [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retourne le quotient complet qui conserve le reste dans la partie fractionnaire.  
  
## Notes  
 Avant d'exécuter la division, Visual Basic tente de convertir toute expression numérique à virgule flottante en `Long`.  Si `Option Strict` est `On`, une erreur du compilateur se produit.  Si `Option Strict` est `Off`, un <xref:System.OverflowException> est possible si la valeur est à l'extérieur de la plage de [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).  La conversion en `Long` est également soumise à l'*arrondi bancaire*.  Pour plus d'informations, consultez « Parties fractionnaires » dans [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Si `expression1` ou `expression2` correspond à [Nothing](../../../visual-basic/language-reference/nothing.md), elle est considérée comme un zéro.  
  
## Essai de division par zéro  
 Si `expression2` correspond à zéro, l'opérateur `\` lève une exception <xref:System.DivideByZeroException>.  Cette règle est valable pour tous les types de données numériques des opérandes.  
  
> [!NOTE]
>  L'opérateur `\` peut être *surchargé*, ce qui signifie qu'une classe ou structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 Cet exemple utilise l'opérateur `\` pour effectuer une division d'entier.  Le résultat est un entier qui représente le quotient entier des deux opérandes avec le reste abandonné.  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 Les expressions dans l'exemple précédent retournent respectivement les valeurs 2 ; 3 ; 33 et \-22.  
  
## Voir aussi  
 [\\\= Operator](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)