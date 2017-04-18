---
title: "Comment : appeler une procédure qui ne retourne pas de valeur (Visual Basic) | Documents Microsoft"
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
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
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
ms.openlocfilehash: 17b2b902f3ee6ab79b2614b7742aa08fefab2420
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Comment : appeler une procédure qui ne retourne pas de valeur (Visual Basic)
Un `Sub` procédure ne retourne pas de valeur au code appelant. Vous l’appelez explicitement avec une instruction d’appel autonome. Vous ne pouvez pas l’appeler en utilisant simplement son nom dans une expression.  
  
### <a name="to-call-a-sub-procedure"></a>Pour appeler une procédure Sub  
  
1.  Spécifiez le nom de la `Sub` procédure.  
  
2.  Suivre le nom de procédure avec des parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses. Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.  
  
3.  Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules. Assurez-vous de fournir les arguments dans le même ordre que les `Sub` procédure définit les paramètres correspondants.  
  
     L’exemple suivant appelle la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>fonction pour activer une fenêtre d’application.</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>accepte le titre de la fenêtre comme unique argument.</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> Il ne retourne pas de valeur au code appelant. Si un processus Notepad n’est pas en cours d’exécution, l’exemple lève un <xref:System.ArgumentException>.</xref:System.ArgumentException> Le `Shell` procédure suppose que les applications se trouvent dans les chemins d’accès spécifiés.  
  
     [!code-vb[VbVbalrCatRef&#11;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A></xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:System.ArgumentException></xref:System.ArgumentException>   
 [Procédures](./index.md)   
 [Procédures Sub](./sub-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Comment : créer une procédure](./how-to-create-a-procedure.md)   
 [Comment : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)   
 [Comment : appeler un gestionnaire d’événements en Visual Basic](./how-to-call-an-event-handler.md)
