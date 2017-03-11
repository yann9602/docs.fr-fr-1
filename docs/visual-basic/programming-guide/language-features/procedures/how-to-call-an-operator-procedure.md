---
title: "How to: Call an Operator Procedure (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator procedures, calling"
  - "procedures, operator"
  - "procedure calls, operator overloading"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "return values, Operator procedures"
  - "overloaded operators, calling"
  - "operator overloading"
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Call an Operator Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous devez appeler une procédure d'opérateur en utilisant le symbole d'opérateur dans une expression.  Dans le cas d'un opérateur de conversion, vous devez l'appeler en appelant la [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) afin de convertir une valeur d'un type de données en un autre.  
  
 Vous ne devez pas appeler pas de procédures d'opérateur explicitement.  Vous utilisez l'opérateur, ou la fonction `CType`, dans une expression ou une instruction d'assignation, comme pour l'utilisation ordinaire d'un opérateur.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] effectue l'appel à la procédure d'opérateur.  
  
 La définition d'un opérateur sur une classe ou une structure est également appelée *surcharge* de l'opérateur.  
  
### Pour appeler une procédure d'opérateur  
  
1.  Utilisez normalement le symbole d'opérateur dans une expression.  
  
2.  Assurez\-vous que les types de données des opérandes sont appropriés pour l'opérateur et dans l'ordre correct.  
  
3.  L'opérateur contribue à la valeur de l'expression comme prévu.  
  
### Pour appeler une procédure d'opérateur de conversion  
  
1.  Utilisez `CType` à l'intérieur d'une expression.  
  
2.  Assurez\-vous que les types de données des opérandes sont appropriés pour la conversion et dans l'ordre correct.  
  
3.  `CType` appelle la procédure d'opérateur de conversion et retourne la valeur convertie.  
  
## Exemple  
 L'exemple suivant crée deux structures <xref:System.TimeSpan>, les ajoute et stocke le résultat dans une troisième structure <xref:System.TimeSpan>.  La structure <xref:System.TimeSpan> définit des procédures d'opérateur pour surcharger plusieurs opérateurs standard.  
  
 [!code-vb[VbVbcnProcedures#29](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-call-an-operator-_1.vb)]  
  
 Étant donné que <xref:System.TimeSpan> surcharge l'opérateur `+` standard, l'exemple précédent appelle une procédure d'opérateur lorsqu'il calcule la valeur de `combinedSpan`.  
  
 Pour obtenir un exemple d'appel de procédure d'opérateur de conversation, consultez [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md).  
  
## Compilation du code  
 Assurez\-vous que la classe ou la structure que vous utilisez définit l'opérateur que vous souhaitez utiliser.  
  
## Voir aussi  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)