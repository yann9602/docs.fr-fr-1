---
title: "How to: Declare a Property with Mixed Access Levels (Visual Basic) | Microsoft Docs"
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
  - "access levels, properties"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "mixed access levels"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], access levels"
  - "Property statement, declaring mixed access levels"
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Declare a Property with Mixed Access Levels (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Si vous souhaitez que les procédures `Get` et `Set` sur une propriété aient différents niveaux d'accès, vous pouvez utiliser le niveau le plus permissif dans l'instruction `Property` et le niveau le plus restrictif dans l'instruction `Get` ou `Set`.  Utilisez des niveaux d'accès mixtes sur une propriété si vous souhaitez que certaines parties du code puissent obtenir la valeur de la propriété et que d'autres parties du code puissent modifier la valeur.  
  
 Pour plus d'informations sur les niveaux d'accès, consultez [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### Pour déclarer une propriété avec des niveaux d'accès mixtes  
  
1.  Déclarez normalement la propriété et spécifiez le niveau d'accès le moins restrictif \(tel que `Public`\) dans l'instruction `Property`.  
  
2.  Déclarez la procédure `Get` ou `Set` spécifiant le niveau d'accès le plus restrictif \(tel que `Friend`\).  
  
3.  Ne spécifiez pas de niveau d'accès sur l'autre procédure de propriété.  Le niveau d'accès déclaré dans l'instruction `Property` est supposé.  Vous pouvez restreindre l'accès sur une seule des procédures de propriété.  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     Dans l'exemple précédent, la procédure `Get` a le même accès `Protected` que la propriété elle\-même, alors que la procédure `Set` a un accès `Private`.  Une classe dérivée de `employee` peut lire la valeur `salary`, mais seule la classe `employee` peut la définir.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)