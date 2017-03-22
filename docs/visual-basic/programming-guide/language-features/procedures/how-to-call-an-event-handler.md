---
title: "Comment : appeler un gestionnaire d’événements en Visual Basic | Documents Microsoft"
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
- event handlers, calling
- event handlers
- procedures, event handlers
- procedures, calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
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
ms.openlocfilehash: c5b300feca3415d1283d24179795a4ae92c61e52
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Comment : appeler un gestionnaire d'événements en Visual Basic
Un *événement* est une action ou une occurrence, tel qu’une souris, clic ou une limite de crédit dépassé : reconnue par un composant de programme pour lequel vous pouvez écrire du code en réponse. Un *Gestionnaire d’événements* est le code que vous écrivez pour répondre à un événement.  
  
 Un gestionnaire d’événements dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] est un `Sub` procédure. Toutefois, vous ne normalement l’appelez pas la même façon que les autres `Sub` procédures. Au lieu de cela, vous identifiez la procédure comme un gestionnaire pour l’événement. Cela avec une [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) clause et un [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, ou avec un [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md). À l’aide un `Handles` clause constitue la méthode par défaut pour déclarer un gestionnaire d’événements dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Il s’agit de la manière dont les gestionnaires d’événements sont écrits par les concepteurs lorsque vous programmez dans l’environnement de développement intégré (IDE). La `AddHandler` instruction convient pour déclencher des événements dynamiquement au moment de l’exécution.  
  
 Lorsque l’événement se produit, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle automatiquement la procédure de gestionnaire d’événements. Tout code qui a accès à l’événement peut déclencher celui-ci en exécutant une [RaiseEvent, instruction](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Vous pouvez associer plusieurs gestionnaires d’événements à l’événement. Dans certains cas, vous pouvez dissocier un gestionnaire d’un événement. Pour plus d’informations, consultez [événements](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Pour appeler un gestionnaire d’événements à l’aide de Handles et WithEvents  
  
1.  Assurez-vous que l’événement est déclaré avec une [Event, instruction](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2.  Déclarez une variable objet au module ou la classe niveau, à l’aide de la [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) (mot clé). Le `As` pour cette variable doit spécifier la classe qui déclenche l’événement.  
  
3.  Dans la déclaration de la gestion des événements `Sub` procédure, ajoutez un [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) clause qui spécifie le `WithEvents` variable et le nom de l’événement.  
  
4.  Lorsque l’événement se produit, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle automatiquement la `Sub` procédure. Votre code peut utiliser un `RaiseEvent` instruction pour rendre l’événement se produit.  
  
     L’exemple suivant définit un événement et une `WithEvents` variable qui fait référence à la classe qui déclenche l’événement. La gestion des événements `Sub` procédure utilise un `Handles` clause pour spécifier la classe et l’événement qu’elle gère.  
  
     [!code-vb[VbVbcnProcedures n °&4;](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>Pour appeler un gestionnaire d’événements à l’aide de AddHandler  
  
1.  Assurez-vous que l’événement est déclaré avec une `Event` instruction.  
  
2.  Exécuter un [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md) connecter dynamiquement la gestion des événements `Sub` procédure avec l’événement.  
  
3.  Lorsque l’événement se produit, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle automatiquement la `Sub` procédure. Votre code peut utiliser un `RaiseEvent` instruction pour rendre l’événement se produit.  
  
     L’exemple suivant définit un `Sub` procédure pour gérer les <xref:System.Windows.Forms.Form.Closing>événement d’un formulaire.</xref:System.Windows.Forms.Form.Closing> Il utilise ensuite la [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md) à associer le `catchClose` procédure comme un gestionnaire d’événements <xref:System.Windows.Forms.Form.Closing>.</xref:System.Windows.Forms.Form.Closing>  
  
     [!code-vb[VbVbcnProcedures n °&5;](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     Vous pouvez dissocier un gestionnaire d’événements à partir d’un événement en exécutant le [RemoveHandler, instruction](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Procédures Sub](./sub-procedures.md)   
 [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [AddressOf (opérateur)](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Comment : créer une procédure](./how-to-create-a-procedure.md)   
 [Guide pratique : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)
