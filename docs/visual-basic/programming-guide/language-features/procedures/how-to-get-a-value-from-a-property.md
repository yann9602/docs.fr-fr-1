---
title: "How to: Get a Value from a Property (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "property values"
  - "Visual Basic code, procedures"
  - "values, properties"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], values"
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Get a Value from a Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous pouvez récupérer la valeur d'une propriété en incluant le nom de propriété dans une expression.  
  
 La procédure `Get` de la propriété récupère la valeur, mais vous ne l'appelez pas explicitement par son nom.  Utilisez la propriété de la même façon qu'une variable.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] se charge d'appeler les procédures de la propriété.  
  
### Pour récupérer une valeur à partir d'une propriété  
  
1.  Utilisez le nom de propriété dans une expression tout comme vous utiliseriez un nom de variable.  Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.  
  
     ou  
  
     Utilisez le nom de propriété qui suit le signe égal \(`=`\) dans une instruction d'assignation.  
  
     L'exemple suivant lit la valeur de la propriété `Now` de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], en appelant sa procédure  `Get` implicitement.  
  
     [!code-vb[VbVbalrDateProperties#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  Si la propriété accepte des arguments, faites suivre le nom de propriété de parenthèses à l'intérieur desquelles vous joindrez la liste d'arguments.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  
  
3.  Placez les arguments dans la liste d'arguments entre parenthèses en les séparant par des virgules.  Assurez\-vous de fournir les arguments dans le même ordre que les paramètres correspondants définis par la propriété.  
  
 La valeur de la propriété participe à l'expression comme le ferait une variable ou une constante, ou bien elle est stockée dans la variable ou la propriété située sur le côté gauche de l'instruction d'assignation.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)