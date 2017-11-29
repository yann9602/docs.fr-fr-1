---
title: "Procédure pas à pas : création de votre première application Touch"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee85a5d8764fc27205cf09e1af43069b25096ef1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-your-first-touch-application"></a><span data-ttu-id="01dbc-102">Procédure pas à pas : création de votre première application Touch</span><span class="sxs-lookup"><span data-stu-id="01dbc-102">Walkthrough: Creating Your First Touch Application</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="01dbc-103">permet aux applications réponde aux entrées tactiles.</span><span class="sxs-lookup"><span data-stu-id="01dbc-103"> enables applications to respond to touch.</span></span> <span data-ttu-id="01dbc-104">Par exemple, vous pouvez interagir avec une application en utilisant l’une ou plusieurs doigts sur un périphérique tactile, par exemple un écran tactile que cette procédure pas à pas crée une application qui permet à l’utilisateur à déplacer, redimensionnement ou faire pivoter un objet unique à l’aide des fonctions tactiles.</span><span class="sxs-lookup"><span data-stu-id="01dbc-104">For example, you can interact with an application by using one or more fingers on a touch-sensitive device, such as a touchscreen This walkthrough creates an application that enables the user to move, resize, or rotate a single object by using touch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="01dbc-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="01dbc-105">Prerequisites</span></span>  
 <span data-ttu-id="01dbc-106">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="01dbc-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]<span data-ttu-id="01dbc-107">.</span><span class="sxs-lookup"><span data-stu-id="01dbc-107">.</span></span>  
  
-   <span data-ttu-id="01dbc-108">Windows 7.</span><span class="sxs-lookup"><span data-stu-id="01dbc-108">Windows 7.</span></span>  
  
-   <span data-ttu-id="01dbc-109">Un périphérique qui accepte une entrée, par exemple un écran tactile, qui prend en charge l’interface tactile Windows tactile.</span><span class="sxs-lookup"><span data-stu-id="01dbc-109">A device that accepts touch input, such as a touchscreen, that supports Windows Touch.</span></span>  
  
 <span data-ttu-id="01dbc-110">En outre, vous devez avoir une compréhension de base de la création d’une application dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], en particulier comment s’abonner à et gérer un événement.</span><span class="sxs-lookup"><span data-stu-id="01dbc-110">Additionally, you should have a basic understanding of how to create an application in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especially how to subscribe to and handle an event.</span></span> <span data-ttu-id="01dbc-111">Pour plus d’informations, consultez [procédure pas à pas : Ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="01dbc-111">For more information, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="creating-the-application"></a><span data-ttu-id="01dbc-112">Création de l’application</span><span class="sxs-lookup"><span data-stu-id="01dbc-112">Creating the Application</span></span>  
  
#### <a name="to-create-the-application"></a><span data-ttu-id="01dbc-113">Pour créer l'application</span><span class="sxs-lookup"><span data-stu-id="01dbc-113">To create the application</span></span>  
  
1.  <span data-ttu-id="01dbc-114">Créez un projet d’application WPF en Visual Basic ou Visual C# nommé `BasicManipulation`.</span><span class="sxs-lookup"><span data-stu-id="01dbc-114">Create a new WPF Application project in Visual Basic or Visual C# named `BasicManipulation`.</span></span> <span data-ttu-id="01dbc-115">Pour plus d'informations, consultez [Guide pratique pour créer un projet d'application WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="01dbc-115">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="01dbc-116">Remplacez le contenu de MainWindow.xaml par le code XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="01dbc-116">Replace the contents of MainWindow.xaml with the following XAML.</span></span>  
  
     <span data-ttu-id="01dbc-117">Ce balisage crée une application simple qui contient une croix rouge <xref:System.Windows.Shapes.Rectangle> sur un <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="01dbc-117">This markup creates a simple application that contains a red <xref:System.Windows.Shapes.Rectangle> on a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="01dbc-118">Le <xref:System.Windows.UIElement.IsManipulationEnabled%2A> propriété de la <xref:System.Windows.Shapes.Rectangle> est définie sur true afin qu’il reçoive les événements de manipulation.</span><span class="sxs-lookup"><span data-stu-id="01dbc-118">The <xref:System.Windows.UIElement.IsManipulationEnabled%2A> property of the <xref:System.Windows.Shapes.Rectangle> is set to true so that it will receive manipulation events.</span></span> <span data-ttu-id="01dbc-119">L’application s’abonne à la <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, et <xref:System.Windows.UIElement.ManipulationInertiaStarting> événements.</span><span class="sxs-lookup"><span data-stu-id="01dbc-119">The application subscribes to the <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, and <xref:System.Windows.UIElement.ManipulationInertiaStarting> events.</span></span> <span data-ttu-id="01dbc-120">Ces événements contiennent la logique pour déplacer le <xref:System.Windows.Shapes.Rectangle> lorsque l’utilisateur manipule.</span><span class="sxs-lookup"><span data-stu-id="01dbc-120">These events contain the logic to move the <xref:System.Windows.Shapes.Rectangle> when the user manipulates it.</span></span>  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  <span data-ttu-id="01dbc-121">Si vous utilisez Visual Basic, dans la première ligne de MainWindow.xaml, remplacez `x:Class="BasicManipulation.MainWindow"` avec `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="01dbc-121">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="BasicManipulation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
4.  <span data-ttu-id="01dbc-122">Dans le `MainWindow` de classe, ajoutez le code suivant <xref:System.Windows.UIElement.ManipulationStarting> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="01dbc-122">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationStarting> event handler.</span></span>  
  
     <span data-ttu-id="01dbc-123">Le <xref:System.Windows.UIElement.ManipulationStarting> événement se produit lorsque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] détecte cette touche entrée commence à manipuler un objet.</span><span class="sxs-lookup"><span data-stu-id="01dbc-123">The <xref:System.Windows.UIElement.ManipulationStarting> event occurs when [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detects that touch input begins to manipulate an object.</span></span> <span data-ttu-id="01dbc-124">Le code spécifie que la position de la manipulation doit être relative à la <xref:System.Windows.Window> en définissant le <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="01dbc-124">The code specifies that the position of the manipulation should be relative to the <xref:System.Windows.Window> by setting the <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> property.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  <span data-ttu-id="01dbc-125">Dans le `MainWindow` de classe, ajoutez le code suivant <xref:System.Windows.Input.ManipulationDelta> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="01dbc-125">In the `MainWindow` class, add the following <xref:System.Windows.Input.ManipulationDelta> event handler.</span></span>  
  
     <span data-ttu-id="01dbc-126">Le <xref:System.Windows.Input.ManipulationDelta> événement se produit lorsque l’entrée tactile modifie la position et peut se produire plusieurs fois pendant une manipulation.</span><span class="sxs-lookup"><span data-stu-id="01dbc-126">The <xref:System.Windows.Input.ManipulationDelta> event occurs when the touch input changes position and can occur multiple times during a manipulation.</span></span> <span data-ttu-id="01dbc-127">L’événement peut également se produire après le déclenche d’un doigt.</span><span class="sxs-lookup"><span data-stu-id="01dbc-127">The event can also occur after a finger is raised.</span></span> <span data-ttu-id="01dbc-128">Par exemple, si l’utilisateur fait glisser un doigt sur un écran, le <xref:System.Windows.Input.ManipulationDelta> événement se produit plusieurs fois en tant que le déplacement du doigt.</span><span class="sxs-lookup"><span data-stu-id="01dbc-128">For example, if the user drags a finger across a screen, the <xref:System.Windows.Input.ManipulationDelta> event occurs multiple times as the finger moves.</span></span> <span data-ttu-id="01dbc-129">Lorsque l’utilisateur enlève un doigt de l’écran, le <xref:System.Windows.Input.ManipulationDelta> événement continue de se produire pour simuler l’inertie.</span><span class="sxs-lookup"><span data-stu-id="01dbc-129">When the user raises a finger from the screen, the <xref:System.Windows.Input.ManipulationDelta> event keeps occurring to simulate inertia.</span></span>  
  
     <span data-ttu-id="01dbc-130">Le code s’applique le <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> à la <xref:System.Windows.UIElement.RenderTransform%2A> de la <xref:System.Windows.Shapes.Rectangle> pour déplacer tandis que l’utilisateur déplace la fonction tactile d’entrée.</span><span class="sxs-lookup"><span data-stu-id="01dbc-130">The code applies the <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> to the <xref:System.Windows.UIElement.RenderTransform%2A> of the <xref:System.Windows.Shapes.Rectangle> to move it as the user moves the touch input.</span></span> <span data-ttu-id="01dbc-131">Il vérifie également si le <xref:System.Windows.Shapes.Rectangle> en dehors des limites de la <xref:System.Windows.Window> lorsque l’événement se produit pendant l’inertie.</span><span class="sxs-lookup"><span data-stu-id="01dbc-131">It also checks whether the <xref:System.Windows.Shapes.Rectangle> is outside the bounds of the <xref:System.Windows.Window> when the event occurs during inertia.</span></span> <span data-ttu-id="01dbc-132">Si, par conséquent, l’application appelle la <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> méthode à la fin de la manipulation.</span><span class="sxs-lookup"><span data-stu-id="01dbc-132">If so, the application calls the <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> method to end the manipulation.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  <span data-ttu-id="01dbc-133">Dans le `MainWindow` de classe, ajoutez le code suivant <xref:System.Windows.UIElement.ManipulationInertiaStarting> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="01dbc-133">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationInertiaStarting> event handler.</span></span>  
  
     <span data-ttu-id="01dbc-134">Le <xref:System.Windows.UIElement.ManipulationInertiaStarting> événement se produit lorsque l’utilisateur déclenche tous les doigts de l’écran.</span><span class="sxs-lookup"><span data-stu-id="01dbc-134">The <xref:System.Windows.UIElement.ManipulationInertiaStarting> event occurs when the user raises all fingers from the screen.</span></span> <span data-ttu-id="01dbc-135">Le code définit la rapidité initiale et la décélération pour le déplacement, d’extension et de rotation du rectangle.</span><span class="sxs-lookup"><span data-stu-id="01dbc-135">The code sets the initial velocity and deceleration for the movement, expansion, and rotation of the rectangle.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  <span data-ttu-id="01dbc-136">Générez et exécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="01dbc-136">Build and run the project.</span></span>  
  
     <span data-ttu-id="01dbc-137">Vous devez voir un carré rouge apparaît dans la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="01dbc-137">You should see a red square appear in the window.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="01dbc-138">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="01dbc-138">Testing the Application</span></span>  
 <span data-ttu-id="01dbc-139">Pour tester l’application, essayez les manipulations suivantes.</span><span class="sxs-lookup"><span data-stu-id="01dbc-139">To test the application, try the following manipulations.</span></span> <span data-ttu-id="01dbc-140">Notez que vous pouvez effectuer plusieurs des opérations suivantes en même temps.</span><span class="sxs-lookup"><span data-stu-id="01dbc-140">Note that you can do more than one of the following at the same time.</span></span>  
  
-   <span data-ttu-id="01dbc-141">Pour déplacer le <xref:System.Windows.Shapes.Rectangle>, mettez un doigt sur le <xref:System.Windows.Shapes.Rectangle> et déplacez le doigt sur l’écran.</span><span class="sxs-lookup"><span data-stu-id="01dbc-141">To move the <xref:System.Windows.Shapes.Rectangle>, put a finger on the <xref:System.Windows.Shapes.Rectangle> and move the finger across the screen.</span></span>  
  
-   <span data-ttu-id="01dbc-142">Pour redimensionner le <xref:System.Windows.Shapes.Rectangle>, placez deux doigts sur le <xref:System.Windows.Shapes.Rectangle> et rapprochez-les ou loin indépendamment les uns des autres.</span><span class="sxs-lookup"><span data-stu-id="01dbc-142">To resize the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and move the fingers closer together or farther apart from each other.</span></span>  
  
-   <span data-ttu-id="01dbc-143">Pour faire pivoter le <xref:System.Windows.Shapes.Rectangle>, placez deux doigts sur le <xref:System.Windows.Shapes.Rectangle> et faites pivoter les doigts autour de l’autre.</span><span class="sxs-lookup"><span data-stu-id="01dbc-143">To rotate the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and rotate the fingers around each other.</span></span>  
  
 <span data-ttu-id="01dbc-144">Pour provoquer l’inertie, enlevez rapidement vos doigts à partir de l’écran que vous exécutez les manipulations précédentes.</span><span class="sxs-lookup"><span data-stu-id="01dbc-144">To cause inertia, quickly raise your fingers from the screen as you perform the previous manipulations.</span></span> <span data-ttu-id="01dbc-145">Le <xref:System.Windows.Shapes.Rectangle> continuera à déplacer, redimensionner ou faire pivoter pendant quelques secondes avant de s’arrêter.</span><span class="sxs-lookup"><span data-stu-id="01dbc-145">The <xref:System.Windows.Shapes.Rectangle> will continue to move, resize, or rotate for a few seconds before it stops.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01dbc-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01dbc-146">See Also</span></span>  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
