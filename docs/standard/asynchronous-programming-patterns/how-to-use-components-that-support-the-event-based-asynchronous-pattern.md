---
title: "Comment : utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49e03a8d886ccd4ed6e4b2a19692c1874f5928ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Comment : utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements
De nombreux composants vous donnent la possibilité d’effectuer leur travail de façon asynchrone. Le <xref:System.Media.SoundPlayer> et <xref:System.Windows.Forms.PictureBox> composants, par exemple, vous permet de charger les sons et des images « en arrière-plan » pendant que votre thread principal continue de s’exécuter sans interruption.  
  
 À l’aide des méthodes asynchrones sur une classe qui prend en charge la [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) peut être aussi simple que l’attachement d’un gestionnaire d’événements pour le composant *MethodName* `Completed` événement, comme vous le feriez pour tout autre événement. Lorsque vous appelez le *MethodName* `Async` (méthode), votre application continue à s’exécuter sans interruption jusqu'à ce que le *MethodName* `Completed` événement est déclenché. Dans votre gestionnaire d’événements, vous pouvez examiner le <xref:System.ComponentModel.AsyncCompletedEventArgs> paramètre pour déterminer si l’opération asynchrone est terminée avec succès ou si elle a été annulée.  
  
 Pour plus d’informations sur l’utilisation des gestionnaires d’événements, consultez [vue d’ensemble des gestionnaires d’événements](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 La procédure suivante montre comment utiliser la fonction de chargement d’image asynchrone d’un <xref:System.Windows.Forms.PictureBox> contrôle.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Pour activer un contrôle PictureBox charger une image de façon asynchrone  
  
1.  Créez une instance de la <xref:System.Windows.Forms.PictureBox> composant dans votre formulaire.  
  
2.  Affecter un gestionnaire d’événements pour le <xref:System.Windows.Forms.PictureBox.LoadCompleted> événement.  
  
     Recherchez les erreurs qui se sont produites pendant le téléchargement asynchrone. Il s’agit également lorsque vous vérifiez l’annulation.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  Ajoutez deux boutons, appelés `loadButton` et `cancelLoadButton`, à votre formulaire. Ajouter <xref:System.Windows.Forms.Control.Click> gestionnaires d’événements pour démarrer et d’annuler le téléchargement.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  Exécutez l'application.  
  
     Au fur et à mesure du téléchargement de l’image, vous pouvez déplacer librement le formulaire, réduire et agrandir.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour exécuter une opération en arrière-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NOT IN BUILD : Multithreading en Visual Basic](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)
