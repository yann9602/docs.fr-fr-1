---
title: "How to: Define a Conversion Operator (Visual Basic) | Microsoft Docs"
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
  - "procedures, defining"
  - "operators [Visual Basic], defining"
  - "procedures, operator"
  - "operators [Visual Basic], overloading"
  - "return values, Operator procedures"
  - "operator overloading"
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Define a Conversion Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Si vous avez défini une classe ou  structure, vous pouvez définir un opérateur de conversion du type de votre classe ou structure en un autre type de données \(tel que `Integer`, `Double` ou `String`\).  
  
 Définissez la conversion de type comme une procédure [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) dans la classe ou la structure.  Toutes les procédures de conversion doivent être `Public Shared` et chacune doit spécifier [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) ou [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 La définition d'un opérateur sur une classe ou une structure est également appelée *surcharge* de l'opérateur.  
  
## Exemple  
 L'exemple suivant définit des opérateurs de conversion entre une structure appelée  `digit`  et un `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-define-a-conversi_1.vb)]  
  
 Vous pouvez tester la structure `digit` à l'aide du code suivant.  
  
 [!code-vb[VbVbcnProcedures#28](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-define-a-conversi_2.vb)]  
  
## Voir aussi  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)