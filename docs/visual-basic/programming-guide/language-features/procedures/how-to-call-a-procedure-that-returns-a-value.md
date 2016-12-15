---
title: "How to: Call a Procedure That Returns a Value (Visual Basic) | Microsoft Docs"
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
  - "procedure calls, returning values"
  - "Visual Basic code, procedures"
  - "procedures, calling"
  - "procedures, returning a value"
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Call a Procedure That Returns a Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une procédure `Function` retourne une valeur au code appelant.  Vous l'appelez en incluant son nom et ses arguments à droite d'une instruction d'assignation ou dans une expression.  
  
### Pour appeler une procédure Function dans une expression  
  
1.  Utilisez le nom de procédure `Function` de la même façon que vous utilisez une variable.  Vous pouvez utiliser un appel de procédure `Function` n'importe où vous pouvez utiliser une variable ou une constante dans une expression.  
  
2.  Insérez des parenthèses après le nom de la procédure pour encadrer la liste d'arguments.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  Toutefois les parenthèses simplifient la lecture de votre code.  
  
3.  Placez les arguments dans la liste d'arguments entre parenthèses en les séparant par des virgules.  Assurez\-vous de fournir les arguments dans le même ordre que les paramètres correspondants définis par la procédure `Function`.  
  
     Vous pouvez également passer un ou plusieurs arguments par nom.  Pour plus d'informations, consultez [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
4.  La valeur retournée par la procédure participe à l'expression comme la valeur d'une variable ou d'une constante le ferait.  
  
### Pour appeler une procédure Function dans une instruction d'assignation  
  
1.  Utilisez le nom de procédure `Function` après le signe égal \(`=`\) dans l'instruction d'assignation.  
  
2.  Insérez des parenthèses après le nom de la procédure pour encadrer la liste d'arguments.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  Toutefois les parenthèses simplifient la lecture de votre code.  
  
3.  Placez les arguments dans la liste d'arguments entre parenthèses en les séparant par des virgules.  Assurez\-vous de fournir les arguments dans le même ordre que les paramètres correspondants définis par la procédure `Function`, à moins que vous les passiez par nom.  
  
4.  La valeur retournée par la procédure est stockée dans la variable ou la propriété sur le côté gauche de l'instruction d'assignation.  
  
## Exemple  
 L'exemple suivant appelle [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> pour récupérer la valeur d'une variable d'environnement du système d'exploitation.  La première ligne appelle `Environ` dans une expression et la deuxième ligne l'appelle dans une instruction d'assignation.  `Environ` accepte le nom de variable comme unique argument.  Il retourne la valeur de la variable au code appelant.  
  
 [!code-vb[VbVbcnProcedures#7](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## Voir aussi  
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [How to: Create a Procedure that Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [How to: Return a Value from a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [How to: Call a Procedure that Does Not Return a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)