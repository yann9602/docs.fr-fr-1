---
title: "Comment : appeler une procédure de propriété (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], property procedures
- procedure calls, property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7dd3d53f602886f65c951de34b915b2672b1a817
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Comment : appeler une procédure de propriété (Visual Basic)
Vous appelez une procédure de propriété en stockant une valeur dans la propriété ou de récupérer sa valeur. Vous accédez à une propriété la même façon que vous accédez à une variable.  
  
 La propriété `Set` stocke une valeur et ses `Get` procédure récupère la valeur. Toutefois, vous n’appelez pas explicitement ces procédures par nom. Vous utilisez la propriété dans une instruction d’assignation ou une expression, comme vous stockiez ou récupérer la valeur d’une variable. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]appelle les procédures de propriété.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Pour appeler une procédure Get d’une propriété  
  
1.  Utiliser le nom de propriété dans une expression de la même manière que vous utiliseriez un nom de variable. Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.  
  
     ou  
  
     Utilisez le nom de propriété suivant égaux (`=`) se connecter dans une instruction d’assignation.  
  
     L’exemple suivant lit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>propriété implicitement en appelant son `Get` procédure.</xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
  
     [!code-vb[VbVbalrDateProperties n °&4;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  Si la propriété accepte des arguments, faites suivre le nom de propriété entre parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.  
  
3.  Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules. Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.  
  
 La valeur de la propriété participe à l’expression comme une variable ou constante le ferait, ou il est stocké dans la variable ou la propriété sur le côté gauche de l’instruction d’assignation.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Pour appeler une propriété Set de la procédure  
  
1.  Utilisez le nom de propriété sur le côté gauche d’une instruction d’assignation.  
  
     L’exemple suivant définit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>propriété implicitement en appelant le `Set` procédure.</xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
  
     [!code-vb[VbVbcnProcedures&#11;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  Si la propriété accepte des arguments, faites suivre le nom de propriété entre parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.  
  
3.  Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules. Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.  
  
 La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures de propriété](./property-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md)   
 [Comment : créer une propriété](./how-to-create-a-property.md)   
 [Comment : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)   
 [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)   
 [Comment : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)   
 [Get (instruction)](../../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set (instruction)](../../../../visual-basic/language-reference/statements/set-statement.md)
