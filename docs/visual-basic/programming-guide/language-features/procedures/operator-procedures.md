---
title: "Operator Procedures (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "procedures, operator"
  - "Visual Basic code, operators"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "overloaded operators"
  - "operator overloading"
  - "operator procedures"
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Operator Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une procédure d'opérateur est une série d'instructions [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] qui définissent le comportement d'un opérateur standard \(tel que `*`, `<>` ou `And`\) sur une classe ou structure définie.  Elle est également appelée *surcharge d'opérateur*.  
  
## Quand définir des procédures d'opérateur  
 Lorsque vous avez défini une classe ou structure, vous pouvez déclarer des variables comme étant du type de cette classe ou structure.  Une telle variable doit parfois participer à une opération intégrée à une expression.  Pour ce faire, elle doit être un opérande d'un opérateur.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] définit uniquement des opérateurs sur ses types de données fondamentaux.  Vous pouvez définir le comportement d'un opérateur lorsqu'au moins un des opérandes est du type de votre classe ou structure.  
  
 Pour plus d'informations, consultez [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## Types de procédure d'opérateur  
 Une procédure d'opérateur peut être de l'un des types suivants :  
  
-   Une définition d'un opérateur unaire dans laquelle l'argument est du type de votre classe ou structure.  
  
-   Une définition d'un opérateur binaire dans lequel au moins un des arguments est du type de votre classe ou structure.  
  
-   Une définition d'un opérateur de conversion dans lequel l'argument est du type de votre classe ou structure.  
  
-   Une définition d'un opérateur de conversion qui retourne le type de votre classe ou structure.  
  
 Les opérateurs de conversion sont toujours unaires, et vous utilisez toujours `CType` comme opérateur en cours de définition.  
  
## Syntaxe de déclaration  
 La syntaxe de déclaration d'une procédure d'opérateur est la suivante :  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`   ``  *symboleopérateur*  `(` *operand1*  `[,`  *operand2* `]) As`  *typedonnées*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Utilisez uniquement le mot clé `Widening` ou `Narrowing` sur un opérateur de conversion de type.  Le symbole de l'opérateur est toujours [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) pour un opérateur de conversion de type.  
  
 Vous déclarez deux opérandes pour définir un opérateur binaire, et un seul opérande pour définir un opérateur unaire, y compris un opérateur de conversion de type.  Tous les opérandes doivent être déclarés comme étant `ByVal`.  
  
 Vous déclarez chaque opérande de la même manière que vous déclarez des paramètres pour [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md).  
  
### Type de données  
 Comme vous définissez un opérateur sur une classe ou structure que vous avez définie, au moins un des opérandes doit être du même type de données que cette classe ou structure.  Pour un opérateur de conversion de type, l'opérande ou le type de retour doit être du même type de données que la classe ou structure.  
  
 Pour plus d'informations, consultez [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## Syntaxe d'appel  
 Vous devez appeler de manière implicite une procédure d'opérateur en utilisant le symbole d'opérateur dans une expression.  Vous fournissez les opérandes de la même manière que pour les opérateurs prédéfinis.  
  
 La syntaxe d'un appel implicite à une procédure d'opérateur est la suivante :  
  
 `Dim testStruct As`  *NomStructure*  
  
 `Dim testNewStruct As`  *nomstructure*  `= testStruct`  *symboleopérateur*  `10`  
  
### Illustration de déclaration et d'appel  
 La structure suivante stocke une valeur entière 128 bits signée comme parties constitutives de poids fort et de poids faible.  Elle définit l'opérateur `+` pour ajouter deux valeurs  `veryLong`  et générer une valeur  `veryLong`  résultante.  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 L'exemple suivant montre un appel classique à l'opérateur `+` dont la valeur est  `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 Pour plus d'informations et d'exemples, consultez la page [Surcharge d'opérateur dans Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703) \(en anglais\).  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)