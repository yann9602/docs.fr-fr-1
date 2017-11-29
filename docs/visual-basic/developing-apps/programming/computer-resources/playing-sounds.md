---
title: Lecture de sons (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be5cec634482bf99ddff4ff6b6af8e897c4909e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="playing-sounds-visual-basic"></a>Lecture de sons (Visual Basic)
L’objet `My.Computer.Audio` fournit des méthodes permettant de lire des sons.  
  
## <a name="playing-sounds"></a>Lecture de sons  
 Avec la lecture en arrière-plan, l’application peut exécuter du code pendant la lecture d’un son. La méthode `My.Computer.Audio.Play` permet à l’application de lire un seul fond sonore à la fois. Quand elle lit un nouveau fond sonore, l’application arrête la lecture du fond sonore précédent. L’application peut également lire un son et attendre qu’il s’arrête.  
  
 Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit un son. Quand `AudioPlayMode.WaitToComplete` est spécifié, `My.Computer.Audio.Play` attend que le son s’arrête pour que l’exécution du code appelant continue. Si vous utilisez cet exemple, assurez-vous que le nom de fichier fait référence à un fichier son .wav enregistré sur votre ordinateur  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit un son. Si vous utilisez cet exemple, assurez-vous que les ressources d’application incluent un fichier son .wav nommé Waterfall.  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>Lecture de sons en boucle  
 Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit le son spécifié en arrière-plan quand `PlayMode.BackgroundLoop` est spécifié. Si vous utilisez cet exemple, assurez-vous que le nom de fichier fait référence à un fichier son .wav enregistré sur votre ordinateur.  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit le son spécifié en arrière-plan quand `PlayMode.BackgroundLoop` est spécifié. Si vous utilisez cet exemple, assurez-vous que les ressources d’application incluent un fichier son .wav nommé Waterfall.  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 L’exemple de code précédent est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Son**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
 En général, quand une application lit un son en boucle, elle doit finir par l’arrêter.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Arrêt de la lecture de sons en arrière-plan  
 Utilisez la méthode `My.Computer.Audio.Stop` pour arrêter la lecture en arrière-plan ou en boucle d’un son dans l’application.  
  
 En général, quand une application lit un son en boucle, elle doit l’arrêter à un certain point.  
  
 L’exemple suivant arrête un son qui est lu en arrière-plan.  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 L’exemple de code précédent est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Son**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Lecture de sons système  
 Utilisez la méthode `My.Computer.Audio.PlaySystemSound` pour lire le son système spécifié.  
  
 La méthode `My.Computer.Audio.PlaySystemSound` prend comme paramètre l’un des membres partagés de la classe <xref:System.Media.SystemSound>. Le son système <xref:System.Media.SystemSounds.Asterisk%2A> indique généralement des erreurs.  
  
 L’exemple suivant utilise la méthode `My.Computer.Audio.PlaySystemSound` pour lire un son système.  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Audio>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>  
 <xref:Microsoft.VisualBasic.AudioPlayMode>
