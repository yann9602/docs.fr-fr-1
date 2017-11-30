---
title: "Comment : appeler un gestionnaire d'événements en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52b4b6ca8b03d8301535d6aeedc3bd0190d8527f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Comment : appeler un gestionnaire d'événements en Visual Basic
Un *événement* est une action ou une occurrence, telles que la souris, cliquez ou une limite de crédit dépassé : reconnue par un composant de programme pour lequel vous pouvez écrire du code en réponse. Un *Gestionnaire d’événements* est le code que vous écrivez pour répondre à un événement.  
  
 Un gestionnaire d’événements dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] est un `Sub` procédure. Toutefois, vous ne normalement l’appelez pas la même façon que d’autres `Sub` procédures. Au lieu de cela, vous identifiez la procédure comme gestionnaire pour l’événement. Vous pouvez effectuer ceci avec un [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) clause et un [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, ou avec un [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md). À l’aide un `Handles` clause constitue la méthode par défaut de déclarer un gestionnaire d’événements dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Il s’agit de la manière dont les gestionnaires d’événements sont écrits par les concepteurs lorsque vous programmez dans l’environnement de développement intégré (IDE). La `AddHandler` instruction convient pour déclencher des événements de manière dynamique au moment de l’exécution.  
  
 Lorsque l’événement se produit, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] appelle automatiquement la procédure de gestionnaire d’événements. Tout code qui a accès à l’événement peut déclencher celui-ci en exécutant une [RaiseEvent, instruction](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Vous pouvez associer plusieurs gestionnaires d’événements avec le même événement. Dans certains cas, vous pouvez dissocier un gestionnaire d’un événement. Pour plus d’informations, consultez [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Pour appeler un gestionnaire d’événements à l’aide de Handles et WithEvents  
  
1.  Assurez-vous que l’événement est déclaré avec un [Event, instruction](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2.  Déclarez une variable objet au module ou la classe niveau, à l’aide de la [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) (mot clé). Le `As` clause pour cette variable doit spécifier la classe qui déclenche l’événement.  
  
3.  Dans la déclaration de la gestion des événements `Sub` procédure, ajoutez un [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) clause qui spécifie le `WithEvents` variable et le nom de l’événement.  
  
4.  Lorsque l’événement se produit, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] appelle automatiquement la `Sub` procédure. Votre code peut utiliser un `RaiseEvent` instruction pour rendre l’événement se produit.  
  
     L’exemple suivant définit un événement et un `WithEvents` variable qui fait référence à la classe qui déclenche l’événement. La gestion des événements `Sub` procédure utilise un `Handles` clause pour spécifier la classe et l’événement qu’elle gère.  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>Pour appeler un gestionnaire d’événements à l’aide de AddHandler  
  
1.  Assurez-vous que l’événement est déclaré avec un `Event` instruction.  
  
2.  Exécuter un [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md) connecter dynamiquement la gestion des événements `Sub` procédure avec l’événement.  
  
3.  Lorsque l’événement se produit, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] appelle automatiquement la `Sub` procédure. Votre code peut utiliser un `RaiseEvent` instruction pour rendre l’événement se produit.  
  
     L’exemple suivant définit un `Sub` procédure pour gérer les <xref:System.Windows.Forms.Form.Closing> événement d’un formulaire. Il utilise ensuite la [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md) pour associer le `catchClose` procédure comme gestionnaire d’événements pour <xref:System.Windows.Forms.Form.Closing>.  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     Vous pouvez dissocier un gestionnaire d’événements à partir d’un événement en exécutant le [RemoveHandler, instruction](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Procédures Sub](./sub-procedures.md)  
 [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [AddressOf (opérateur)](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Guide pratique : créer une procédure](./how-to-create-a-procedure.md)  
 [Guide pratique : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)
