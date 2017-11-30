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
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="39180-102">Comment : utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="39180-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="39180-103">De nombreux composants vous donnent la possibilité d’effectuer leur travail de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="39180-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="39180-104">Le <xref:System.Media.SoundPlayer> et <xref:System.Windows.Forms.PictureBox> composants, par exemple, vous permet de charger les sons et des images « en arrière-plan » pendant que votre thread principal continue de s’exécuter sans interruption.</span><span class="sxs-lookup"><span data-stu-id="39180-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="39180-105">À l’aide des méthodes asynchrones sur une classe qui prend en charge la [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) peut être aussi simple que l’attachement d’un gestionnaire d’événements pour le composant *MethodName* `Completed` événement, comme vous le feriez pour tout autre événement.</span><span class="sxs-lookup"><span data-stu-id="39180-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's *MethodName*`Completed` event, just as you would for any other event.</span></span> <span data-ttu-id="39180-106">Lorsque vous appelez le *MethodName* `Async` (méthode), votre application continue à s’exécuter sans interruption jusqu'à ce que le *MethodName* `Completed` événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="39180-106">When you call the *MethodName*`Async` method, your application will continue running without interruption until the *MethodName*`Completed` event is raised.</span></span> <span data-ttu-id="39180-107">Dans votre gestionnaire d’événements, vous pouvez examiner le <xref:System.ComponentModel.AsyncCompletedEventArgs> paramètre pour déterminer si l’opération asynchrone est terminée avec succès ou si elle a été annulée.</span><span class="sxs-lookup"><span data-stu-id="39180-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="39180-108">Pour plus d’informations sur l’utilisation des gestionnaires d’événements, consultez [vue d’ensemble des gestionnaires d’événements](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="39180-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="39180-109">La procédure suivante montre comment utiliser la fonction de chargement d’image asynchrone d’un <xref:System.Windows.Forms.PictureBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="39180-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="39180-110">Pour activer un contrôle PictureBox charger une image de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="39180-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1.  <span data-ttu-id="39180-111">Créez une instance de la <xref:System.Windows.Forms.PictureBox> composant dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="39180-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2.  <span data-ttu-id="39180-112">Affecter un gestionnaire d’événements pour le <xref:System.Windows.Forms.PictureBox.LoadCompleted> événement.</span><span class="sxs-lookup"><span data-stu-id="39180-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="39180-113">Recherchez les erreurs qui se sont produites pendant le téléchargement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="39180-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="39180-114">Il s’agit également lorsque vous vérifiez l’annulation.</span><span class="sxs-lookup"><span data-stu-id="39180-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  <span data-ttu-id="39180-115">Ajoutez deux boutons, appelés `loadButton` et `cancelLoadButton`, à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="39180-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="39180-116">Ajouter <xref:System.Windows.Forms.Control.Click> gestionnaires d’événements pour démarrer et d’annuler le téléchargement.</span><span class="sxs-lookup"><span data-stu-id="39180-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="39180-117">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="39180-117">Run your application.</span></span>  
  
     <span data-ttu-id="39180-118">Au fur et à mesure du téléchargement de l’image, vous pouvez déplacer librement le formulaire, réduire et agrandir.</span><span class="sxs-lookup"><span data-stu-id="39180-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39180-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39180-119">See Also</span></span>  
 [<span data-ttu-id="39180-120">Guide pratique pour exécuter une opération en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="39180-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="39180-121">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="39180-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="39180-122">NOT IN BUILD : Multithreading en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39180-122">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)
