---
title: "Comment : appeler une procédure qui retourne une valeur (Visual Basic) | Documents Microsoft"
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
- procedures, returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: df6bb1ed8acf5f86a290d67fec9c053cfe5245d2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Comment : appeler une procédure qui retourne une valeur (Visual Basic)
Un `Function` procédure retourne une valeur au code appelant. Vous l’appeler en incluant son nom et ses arguments soit à droite d’une instruction d’assignation ou dans une expression.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Pour appeler une procédure Function dans une expression  
  
1.  Utilisez la `Function` la même manière que vous utiliseriez une variable de nom de la procédure. Vous pouvez utiliser un `Function` partout où vous pouvez utiliser une variable ou une constante dans une expression d’appel de procédure.  
  
2.  Suivre le nom de procédure avec des parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses. Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.  
  
3.  Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules. Assurez-vous de fournir les arguments dans le même ordre que les `Function` procédure définit les paramètres correspondants.  
  
     Vous pouvez également passer un ou plusieurs arguments par nom. Pour plus d’informations, consultez [en passant les Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md).  
  
4.  La valeur retournée par la procédure participe à l’expression comme la valeur d’une variable ou constante le ferait.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Pour appeler une procédure Function dans une instruction d’assignation  
  
1.  Utilisez le `Function` nom de procédure suivant égaux (`=`) connectez-vous à l’instruction d’assignation.  
  
2.  Suivre le nom de procédure avec des parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses. Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.  
  
3.  Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules. Assurez-vous de fournir les arguments dans le même ordre que les `Function` procédure définit les paramètres correspondants, à moins que vous les passiez par nom.  
  
4.  La valeur retournée par la procédure est stockée dans la variable ou la propriété sur le côté gauche de l’instruction d’assignation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant appelle la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A>pour récupérer la valeur d’une variable d’environnement de système d’exploitation.</xref:Microsoft.VisualBasic.Interaction.Environ%2A> La première ligne appelle `Environ` au sein d’une expression et la deuxième ligne l’appelle dans une instruction d’assignation. `Environ`prend le nom de variable comme unique argument. Elle retourne la valeur de la variable au code appelant.  
  
 [!code-vb[VbVbcnProcedures&#7;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures Function](./function-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Comment : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)   
 [Comment : retourner une valeur d’une procédure](./how-to-return-a-value-from-a-procedure.md)   
 [Guide pratique : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)
