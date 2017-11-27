---
title: "Comment : appeler une procédure qui retourne une valeur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f6d408eed67fa417f42252bb49ecea28d4458382
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Comment : appeler une procédure qui retourne une valeur (Visual Basic)
A `Function` procédure retourne une valeur au code appelant. Vous appeler en incluant son nom et ses arguments soit à droite d’une instruction d’assignation ou dans une expression.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Pour appeler une procédure de fonction dans une expression  
  
1.  Utilisez le `Function` la même manière que vous utiliseriez une variable de nom de la procédure. Vous pouvez utiliser un `Function` partout où vous pouvez utiliser une variable ou une constante dans une expression d’appel de procédure.  
  
2.  Suivez le nom de la procédure avec des parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses. Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.  
  
3.  Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules. Assurez-vous de fournir les arguments dans le même ordre que les `Function` procédure définit les paramètres correspondants.  
  
     Ou bien, vous pouvez passer un ou plusieurs arguments par nom. Pour plus d’informations, consultez [en passant les Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md).  
  
4.  La valeur retournée par la procédure participe à l’expression comme la valeur d’une variable ou constante le ferait.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Pour appeler une procédure Function dans une instruction d’assignation  
  
1.  Utilisez le `Function` nom de la procédure suivante égaux (`=`) connectez-vous à l’instruction d’assignation.  
  
2.  Suivez le nom de la procédure avec des parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses. Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.  
  
3.  Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules. Assurez-vous de fournir les arguments dans le même ordre que les `Function` procédure définit les paramètres correspondants, sauf si vous les passez par nom.  
  
4.  La valeur retournée par la procédure est stockée dans la variable ou une propriété sur le côté gauche de l’instruction d’assignation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant appelle la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> pour récupérer la valeur d’une variable d’environnement de système d’exploitation. La première ligne appelle `Environ` au sein d’une expression et la deuxième ligne l’appelle dans une instruction d’assignation. `Environ`prend le nom de variable comme unique argument. Elle retourne la valeur de la variable au code appelant.  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures Function](./function-procedures.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Guide pratique : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Guide pratique : retourner une valeur d’une procédure](./how-to-return-a-value-from-a-procedure.md)  
 [Guide pratique : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)
