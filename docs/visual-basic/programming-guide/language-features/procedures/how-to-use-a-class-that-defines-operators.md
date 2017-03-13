---
title: "How to: Use a Class that Defines Operators (Visual Basic) | Microsoft Docs"
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
  - "procedures, calling"
  - "examples [Visual Basic], CType"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "return values, Operator procedures"
  - "operator overloading"
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# How to: Use a Class that Defines Operators (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Si vous utilisez une classe ou structure qui définit ses propres opérateurs, vous pouvez accéder à ces opérateurs depuis [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
 La définition d'un opérateur sur une classe ou une structure est également appelée *surcharge* de l'opérateur.  
  
## Exemple  
 L'exemple suivant accède à la structure SQL <xref:System.Data.SqlTypes.SqlString> qui définit les opérateurs de conversion \([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)\) dans les deux sens entre une chaîne SQL et une chaîne [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  Utilisez `CType(`*expression de chaîne SQL*, `String)` pour convertir une chaîne SQL en une chaîne [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] et `CType(`*expression de chaîne Visual Basic* pour <xref:System.Data.SqlTypes.SqlString>`)` effectuer la conversion inverse.  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 La structure <xref:System.Data.SqlTypes.SqlString> modifie la valeur d'un opérateur de conversion \([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)\) de `String` à <xref:System.Data.SqlTypes.SqlString> ainsi que la valeur d'un autre opérateur de conversion de <xref:System.Data.SqlTypes.SqlString> à `String`.  L'instruction qui assigne `title` à `jobTitle` utilise le premier opérateur et l'appel de fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> utilise le second.  
  
## Compilation du code  
 Assurez\-vous que la classe ou la structure que vous utilisez définit l'opérateur que vous souhaitez utiliser.  Ne partez pas du principe que la classe ou la structure a défini chaque opérateur comme disponible pour la surcharge.  Pour obtenir la liste des opérateurs disponibles, consultez [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Incluez l'instruction `Imports` appropriée pour la chaîne SQL au début de votre fichier source \(dans le cas présent, <xref:System.Data.SqlTypes>\).  
  
 Votre projet doit comporter des références à System.Data et System.XML.  
  
## Voir aussi  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)