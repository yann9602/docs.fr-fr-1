---
title: "How to: Create a Procedure that Returns a Value (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "procedures, returning a value"
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Create a Procedure that Returns a Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous utilisez une procédure `Function` pour retourner une valeur au code appelant.  
  
### Pour créer une procédure qui retourne une valeur  
  
1.  En dehors de toute autre procédure, utilisez une instruction `Function`, suivie d'une instruction `End Function`  
  
2.  Dans l'instruction `Function`, faites suivre le mot clé `Function` du nom de la procédure, puis de la liste de paramètres entre parenthèses.  
  
3.  Faites suivre les parenthèses d'une clause `As` pour spécifier le type de données de la valeur retournée.  
  
4.  Placez les instructions de code de la procédure entre les instructions `Function` et `End Function`  
  
5.  Utilisez une instruction `Return` pour retourner la valeur au code appelant.  
  
     La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d'un triangle rectangle, d'après les valeurs des deux autres côtés.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     L'exemple suivant montre un appel typique à  `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [How to: Return a Value from a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)