---
title: "How to: Use Components That Support the Event-based Asynchronous Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "Asynchronous Pattern"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "components [.NET Framework], asynchronous"
  - "AsyncOperation class"
  - "threading [Windows Forms], asynchronous features"
  - "AsyncCompletedEventArgs class"
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Use Components That Support the Event-based Asynchronous Pattern
De nombreux composants vous permettent d'exécuter leur travail de manière asynchrone.  Par exemple, les composants <xref:System.Media.SoundPlayer> et <xref:System.Windows.Forms.PictureBox> vous permettent de charger « en arrière\-plan » des sons et des images alors que l'exécution de votre thread principal se poursuit sans interruption.  
  
 L'utilisation des méthodes asynchrones sur une classe qui prend en charge [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) peut être aussi simple que de joindre un gestionnaire d'événements à l'événement du composant *MethodName*`Completed`, ou tout autre événement.  Lorsque vous appelez la méthode *MethodName*`Async`, votre application continue à s'exécuter sans interruption jusqu'à ce que l'événement *MethodName*`Completed` soit déclenché.  Dans votre gestionnaire d'événements, vous pouvez examiner le paramètre <xref:System.ComponentModel.AsyncCompletedEventArgs> pour déterminer si l'opération asynchrone s'est déroulée correctement ou si elle a été annulée.  
  
 Pour plus d'informations sur l'utilisation de gestionnaires d'événements, consultez [Vue d'ensemble des gestionnaires d'événements](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 La procédure suivante indique comment utiliser la fonction de chargement d'image asynchrone d'un contrôle <xref:System.Windows.Forms.PictureBox>.  
  
### Permettre à un contrôle PictureBox de charger une image de manière asynchrone  
  
1.  Créez une instance du composant <xref:System.Windows.Forms.PictureBox> dans votre formulaire.  
  
2.  Assignez un gestionnaire d'événements à l'événement <xref:System.Windows.Forms.PictureBox.LoadCompleted>.  
  
     Recherchez toutes les erreurs qui ont pu se produire pendant le téléchargement asynchrone.  Contrôlez également l'annulation.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  Ajoutez deux boutons, nommés `loadButton` et `cancelLoadButton`, à votre formulaire.  Ajoutez les gestionnaires d'événements <xref:System.Windows.Forms.Control.Click> pour lancer et annuler le téléchargement.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  Exécutez votre application.  
  
     Au cours du téléchargement de l'image, vous pouvez déplacer librement le formulaire, le réduire et l'agrandir.  
  
## Voir aussi  
 [Comment : exécuter une opération en arrière\-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/fr-fr/c731a50c-09c1-4468-9646-54c86b75d269)