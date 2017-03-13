---
title: "How to: Call a Procedure that Does Not Return a Value (Visual Basic) | Microsoft Docs"
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
  - "procedure calls, returning values"
  - "Visual Basic code, procedures"
  - "procedures, calling"
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# How to: Call a Procedure that Does Not Return a Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La procédure `Sub` ne retourne pas de valeur au code appelant.  Vous appelez cette procédure de manière explicite à l'aide d'une instruction d'appel autonome.  Vous ne pouvez pas l'appeler en utilisant uniquement son nom dans une expression.  
  
### Pour appeler une procédure Sub  
  
1.  Spécifiez le nom de la procédure d' `Sub` .  
  
2.  Insérez des parenthèses après le nom de la procédure pour encadrer la liste d'arguments.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  Toutefois les parenthèses simplifient la lecture de votre code.  
  
3.  Placez les arguments dans la liste d'arguments entre parenthèses en les séparant par des virgules.  Assurez\-vous de fournir les arguments dans le même ordre que les paramètres correspondants définis par la procédure `Sub`.  
  
     L'exemple suivant appelle la fonction <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] pour activer une fenêtre d'application.  <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> accepte le titre de la fenêtre comme unique argument.  Elle ne retourne pas de valeur au code appelant.  Si un processus Notepad n'est pas en cours d'exécution, l'exemple lève un <xref:System.ArgumentException>.  La procédure `Shell` suppose que les applications se trouvent dans les chemins d'accès spécifiés.  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:System.ArgumentException>   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [How to: Create a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)   
 [How to: Call an Event Handler in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-event-handler.md)