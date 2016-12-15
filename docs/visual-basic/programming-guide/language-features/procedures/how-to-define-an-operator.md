---
title: "How to: Define an Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "operators [Visual Basic], defining"
  - "procedures, operator"
  - "Visual Basic code, operators"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "operator procedures, about operator procedures"
  - "return values, Operator procedures"
  - "operator overloading"
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Define an Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Si vous avez défini une classe ou une structure, vous pouvez définir le comportement d'un opérateur standard \(tel que `*`, `<>` ou `And`\) lorsqu'au moins une des opérandes est du même type que votre classe ou structure.  
  
 Définissez l'opérateur standard comme une procédure d'opérateur dans la classe ou structure.  Toutes les procédures d'opérateur doivent être `Public` `Shared`.  
  
 La définition d'un opérateur sur une classe ou une structure est également appelée *surcharge* de l'opérateur.  
  
## Exemple  
 L'exemple suivant définit l'opérateur `+` pour une structure appelée  `height`.  La structure utilise des hauteurs exprimées en pieds et pouces.  Un *pouce* équivaut à 2,54 centimètres et un *pied* équivaut à 12 pouces.  Pour garantir des valeurs normalisées \(pouces \< 12,0\), le constructeur exécute une arithmétique *modulo* 12.  L'opérateur `+` utilise le constructeur pour générer des valeurs normalisées.  
  
 [!code-vb[VbVbcnProcedures#25](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 Vous pouvez tester la structure  `height`  à l'aide du code suivant.  
  
 [!code-vb[VbVbcnProcedures#26](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 Pour plus d'informations et d'exemples, consultez la page [Surcharge d'opérateur dans Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703) \(en anglais\).  
  
## Voir aussi  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Mod, opérateur](../../../../visual-basic/language-reference/operators/mod-operator.md)