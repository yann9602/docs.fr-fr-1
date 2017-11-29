---
title: Guide pratique pour enregistrer des exceptions en Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 320bc5d06f4c8e673745b600fd369af287fe8105
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Guide pratique pour enregistrer des exceptions en Visual Basic
Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les exceptions qui se produisent dans votre application. Ces exemples montrent comment utiliser la méthode `My.Application.Log.WriteException` pour enregistrer des exceptions que vous interceptez explicitement et des exceptions qui ne sont pas gérées.  
  
 Pour enregistrer des informations de traçage, utilisez la méthode `My.Application.Log.WriteEntry`. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
  
### <a name="to-log-a-handled-exception"></a>Pour enregistrer une exception gérée  
  
1.  Créez la méthode qui génère les informations sur l’exception.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  Utilisez un bloc `Try...Catch` pour intercepter l’exception.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  Placez le code susceptible de générer une exception dans le bloc `Try`.  
  
     Supprimez les commentaires des lignes `Dim` et `MsgBox` pour déclencher une exception <xref:System.NullReferenceException>.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  Dans le bloc `Catch`, utilisez la méthode `My.Application.Log.WriteException` pour écrire les informations sur l’exception.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     L’exemple suivant montre le code complet permettant d’enregistrer une exception gérée.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a>Pour enregistrer une exception non gérée  
  
1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet** , choisissez **Propriétés**.  
  
2.  Cliquez sur l’onglet **Application** .  
  
3.  Cliquez sur le bouton **Afficher les événements de l’application** pour ouvrir l’éditeur de code.  
  
     Le fichier ApplicationEvents.vb s’ouvre.  
  
4.  Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code. Dans le menu **Général** , choisissez **Événements MyApplication**.  
  
5.  Dans le menu **Déclarations**, choisissez **UnhandledException**.  
  
     L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> avant l’exécution de l’application principale.  
  
6.  Ajoutez la méthode `My.Application.Log.WriteException` au gestionnaire d’événements `UnhandledException` .  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     L’exemple suivant montre le code complet permettant d’enregistrer une exception non gérée.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Guide pratique : écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [Procédure pas à pas : modification de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
