---
title: "How to: Call a Property Procedure (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "Visual Basic code, properties"
  - "procedures, calling"
  - "properties [Visual Basic], property procedures"
  - "procedure calls, property procedures"
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Call a Property Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Appelez une procédure de propriété en stockant une valeur dans la propriété ou en récupérant sa valeur.  Accédez à une propriété de la même manière que vous accédez à une variable.  
  
 La procédure `Set` de la propriété stocke une valeur, et sa procédure `Get` récupère la valeur.  Toutefois n'appelez pas explicitement ces procédures par leur nom.  Utilisez la propriété dans une instruction d'assignation ou une expression, comme si vous stockiez ou récupériez la valeur d'une variable.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] se charge d'appeler les procédures de la propriété.  
  
### Pour appeler la procédure Get d'une propriété  
  
1.  Utilisez le nom de propriété dans une expression tout comme vous utiliseriez un nom de variable.  Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.  
  
     ou  
  
     Utilisez le nom de propriété qui suit le signe égal \(`=`\) dans une instruction d'assignation.  
  
     L'exemple suivant permet de lire la valeur de la propriété <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> en appelant  implicitement sa procédure `Get`.  
  
     [!code-vb[VbVbalrDateProperties#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  Si la propriété accepte des arguments, faites suivre le nom de propriété de parenthèses à l'intérieur desquelles vous joindrez la liste d'arguments.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  
  
3.  Placez les arguments dans la liste d'arguments entre parenthèses en les séparant par des virgules.  Assurez\-vous de fournir les arguments dans le même ordre que les paramètres correspondants définis par la propriété.  
  
 La valeur de la propriété participe à l'expression comme le ferait une variable ou une constante, ou bien elle est stockée dans la variable ou la propriété située sur le côté gauche de l'instruction d'assignation.  
  
### Pour appeler la procédure Set d'une propriété  
  
1.  Spécifiez le nom de la propriété sur le côté gauche d'une instruction d'assignation.  
  
     L'exemple suivant permet de définir la valeur de la propriété <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> en appelant implicitement la procédure `Set`.  
  
     [!code-vb[VbVbcnProcedures#11](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  Si la propriété accepte des arguments, faites suivre le nom de propriété de parenthèses à l'intérieur desquelles vous joindrez la liste d'arguments.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  
  
3.  Placez les arguments dans la liste d'arguments entre parenthèses en les séparant par des virgules.  Assurez\-vous de fournir les arguments dans le même ordre que les paramètres correspondants définis par la propriété.  
  
 La valeur générée sur le côté droit de l'instruction d'assignation est stockée dans la propriété.  
  
## Voir aussi  
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)   
 [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)