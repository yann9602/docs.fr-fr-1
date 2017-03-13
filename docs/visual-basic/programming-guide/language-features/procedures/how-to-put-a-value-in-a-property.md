---
title: "How to: Put a Value in a Property (Visual Basic) | Microsoft Docs"
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
  - "property values"
  - "Visual Basic code, procedures"
  - "values, properties"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], values"
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Put a Value in a Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez stocker une valeur dans une propriété en plaçant le nom de la propriété sur le côté gauche d'une instruction d'assignation.  
  
 La procédure `Set` de la propriété stocke une valeur, mais vous ne l'appelez pas explicitement par son nom.  Utilisez la propriété de la même façon qu'une variable.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] se charge d'appeler les procédures de la propriété.  
  
### Pour stocker une valeur dans une propriété  
  
1.  Spécifiez le nom de la propriété sur le côté gauche d'une instruction d'assignation.  
  
     L'exemple suivant affecte la valeur Midi à la propriété `TimeOfDay` de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], en appelant sa procédure `Set` implicitement.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Si la propriété accepte des arguments, faites suivre le nom de propriété de parenthèses à l'intérieur desquelles vous joindrez la liste d'arguments.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  
  
3.  Placez les arguments dans la liste d'arguments entre parenthèses en les séparant par des virgules.  Assurez\-vous de fournir les arguments dans le même ordre que les paramètres correspondants définis par la propriété.  
  
4.  La valeur générée sur le côté droit de l'instruction d'assignation est stockée dans la propriété.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)