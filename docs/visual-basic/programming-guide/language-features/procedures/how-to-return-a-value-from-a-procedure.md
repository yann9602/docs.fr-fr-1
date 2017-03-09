---
title: "How to: Return a Value from a Procedure (Visual Basic) | Microsoft Docs"
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
  - "procedures, returning from"
  - "procedures, returning a value"
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Return a Value from a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une procédure `Function` retourne une valeur au code appelant en exécutant une instruction  `Return` ou en rencontrant une instruction `Exit Function` ou `End Function`.  
  
### Pour retourner une valeur à l'aide de l'instruction Return  
  
1.  Insérez une instruction `Return` au point où la tâche de la procédure est effectuée.  
  
2.  Faites suivre le mot clé `Return` d'une expression qui cède la valeur que vous souhaitez retourner au code appelant.  
  
3.  Une même procédure peut contenir plusieurs instructions `Return`.  
  
     La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d'un triangle rectangle et le retourne au code appelant.  
  
     [!code-vb[VbVbcnProcedures#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-return-a-value-fr_1.vb)]  
  
     L'exemple suivant présente un appel typique à `hypotenuse` qui stocke la valeur retournée.  
  
     [!code-vb[VbVbcnProcedures#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-return-a-value-fr_2.vb)]  
  
### Pour retourner une valeur à l'aide de la fonction Exit ou End  
  
1.  Assignez une valeur au nom de la procédure à au moins un endroit dans la procédure `Function`.  
  
2.  Lorsque vous exécutez une instruction `Exit Function` ou `End Function`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] retourne la valeur la plus récemment assignée au nom de la procédure.  
  
3.  Une même procédure peut contenir plusieurs instructions `Exit Function` et vous pouvez mixer les instructions `Return` et `Exit Function` dans la même procédure.  
  
4.  Une procédure `Function` peut contenir uniquement une instruction `End Function`.  
  
     Pour plus d'informations, consultez « Valeur de retour » dans [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md)   
 [How to: Create a Procedure that Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)