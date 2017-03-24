---
title: "How to: Create a Procedure (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, reusing"
  - "procedure declarations"
  - "procedures, about procedures"
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# How to: Create a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous insérez une procédure entre une instruction de déclaration initiale \(`Sub` ou `Function`\) et une instruction de la déclaration de la fin \(`End Sub` ou `End Function`\).  Le code de la procédure se trouve entre ces instructions.  
  
 Une procédure ne peut pas contenir une autre procédure, ses instructions de début et de fin doivent donc se situer en dehors de toute autre procédure.  
  
 Si un code effectue la même tâche dans des endroits différents, vous pouvez écrire la tâche une fois en tant que procédure puis l'appeler depuis des endroits différents dans votre code.  
  
### Pour créer une procédure qui ne retourne pas de valeur  
  
1.  En dehors de toute autre procédure, utilisez une instruction `Sub`, suivie d'une instruction `End Sub`  
  
2.  Dans l'instruction `Sub`, faites suivre le mot clé `Sub` du nom de la procédure, puis de la liste de paramètres entre parenthèses.  
  
3.  Placez les instructions de code de la procédure entre les instructions `Sub` et `End Sub`  
  
### Pour créer une procédure qui retourne une valeur  
  
1.  En dehors de toute autre procédure, utilisez une instruction `Function`, suivie d'une instruction `End Function`  
  
2.  Dans l'instruction `Function`, faites suivre le mot clé `Function` du nom de la procédure, puis de la liste de paramètres entre parenthèses, puis d'une clause `As` spécifiant le type de données de la valeur de retour.  
  
3.  Placez les instructions de code de la procédure entre les instructions `Function` et `End Function`  
  
4.  Utilisez une instruction `Return` pour retourner la valeur au code appelant.  
  
### Pour connecter votre nouvelle procédure avec les anciens blocs de code répétitifs  
  
1.  Assurez\-vous que vous définissez la nouvelle procédure dans un endroit auquel l'ancien code a accès.  
  
2.  Dans votre ancien bloc de code répétitif, remplacez les instructions qui effectuent la tâche répétitive par une seule instruction qui appelle la procédure `Sub` ou `Function`.  
  
3.  Si votre procédure est une `Function` qui retourne une valeur, assurez\-vous que votre instruction appelante exécute une action avec la valeur retournée, telle que le stockage dans une variable, dans le cas contraire la valeur sera perdue.  
  
## Exemple  
 La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d'un triangle rectangle, d'après les valeurs des deux autres côtés.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programmation orientée objet dans Visual Basic](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)