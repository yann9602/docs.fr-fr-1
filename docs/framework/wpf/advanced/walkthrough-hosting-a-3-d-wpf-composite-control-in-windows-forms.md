---
title: "Procédure pas à pas : hébergement d'un contrôle composite 3-D WPF dans les Windows Forms"
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
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5af705509d30f7dfd50ade0c07aca242deff4dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="d3076-102">Procédure pas à pas : hébergement d'un contrôle composite 3-D WPF dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3076-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>
<span data-ttu-id="d3076-103">Cette procédure pas à pas montre comment vous pouvez créer un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite de contrôle et l’héberger dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et les contrôles à l’aide de la <xref:System.Windows.Forms.Integration.ElementHost> contrôle.</span><span class="sxs-lookup"><span data-stu-id="d3076-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
 <span data-ttu-id="d3076-104">Dans cette procédure pas à pas, vous allez implémenter un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> qui contient deux contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="d3076-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="d3076-105">Le <xref:System.Windows.Controls.UserControl> affiche un cône tridimensionnel (3D).</span><span class="sxs-lookup"><span data-stu-id="d3076-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="d3076-106">Le rendu d’objets 3D est beaucoup plus facile avec la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à avec [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3076-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="d3076-107">Par conséquent, il convient pour héberger un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> classe pour créer des graphiques 3D dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3076-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="d3076-108">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3076-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="d3076-109">Création de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="d3076-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
-   <span data-ttu-id="d3076-110">Création du projet hôte Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3076-110">Creating the Windows Forms host project.</span></span>  
  
-   <span data-ttu-id="d3076-111">Qui héberge le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="d3076-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
 <span data-ttu-id="d3076-112">Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [qui héberge un contrôle Composite WPF 3D dans les Windows Forms exemple](http://go.microsoft.com/fwlink/?LinkID=160001).</span><span class="sxs-lookup"><span data-stu-id="d3076-112">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a 3-D WPF Composite Control in Windows Forms Sample](http://go.microsoft.com/fwlink/?LinkID=160001).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d3076-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d3076-113">Prerequisites</span></span>  
 <span data-ttu-id="d3076-114">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="d3076-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="d3076-115">.</span><span class="sxs-lookup"><span data-stu-id="d3076-115">.</span></span>  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a><span data-ttu-id="d3076-116">Création du contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="d3076-116">Creating the UserControl</span></span>  
  
#### <a name="to-create-the-usercontrol"></a><span data-ttu-id="d3076-117">Pour créer le UserControl</span><span class="sxs-lookup"><span data-stu-id="d3076-117">To create the UserControl</span></span>  
  
1.  <span data-ttu-id="d3076-118">Créez un projet de bibliothèque de contrôles utilisateur WPF nommé `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="d3076-118">Create a WPF User Control Library project named `HostingWpfUserControlInWf`.</span></span>  
  
2.  <span data-ttu-id="d3076-119">Ouvrez UserControl1.xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3076-119">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
3.  <span data-ttu-id="d3076-120">Remplacez le code généré par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d3076-120">Replace the generated code with the following code.</span></span>  
  
     <span data-ttu-id="d3076-121">Ce code définit un <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> qui contient deux contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="d3076-121">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="d3076-122">Le premier contrôle enfant est un <xref:System.Windows.Controls.Label?displayProperty=nameWithType> contrôle ; le deuxième est un <xref:System.Windows.Controls.Viewport3D> contrôle qui affiche un cône 3D.</span><span class="sxs-lookup"><span data-stu-id="d3076-122">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="d3076-123">Création du projet hôte Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3076-123">Creating the Windows Forms Host Project</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="d3076-124">Pour créer le projet hôte</span><span class="sxs-lookup"><span data-stu-id="d3076-124">To create the host project</span></span>  
  
1.  <span data-ttu-id="d3076-125">Ajouter un projet d’application Windows nommé `WpfUserControlHost` à la solution.</span><span class="sxs-lookup"><span data-stu-id="d3076-125">Add a Windows application project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="d3076-126">Pour plus d'informations, consultez [Guide pratique pour créer un projet d'application WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="d3076-126">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="d3076-127">Dans l’Explorateur de solutions, ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="d3076-127">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="d3076-128">Ajouter des références à ce qui suit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblys :</span><span class="sxs-lookup"><span data-stu-id="d3076-128">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>  
  
    -   <span data-ttu-id="d3076-129">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="d3076-129">PresentationCore</span></span>  
  
    -   <span data-ttu-id="d3076-130">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="d3076-130">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="d3076-131">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="d3076-131">WindowsBase</span></span>  
  
4.  <span data-ttu-id="d3076-132">Ajoutez au projet une référence à `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="d3076-132">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>  
  
5.  <span data-ttu-id="d3076-133">Dans l’Explorateur de solutions, définissez le `WpfUserControlHost` projet comme projet de démarrage.</span><span class="sxs-lookup"><span data-stu-id="d3076-133">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a><span data-ttu-id="d3076-134">Qui héberge le contrôle utilisateur de Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="d3076-134">Hosting the Windows Presentation Foundation UserControl</span></span>  
  
#### <a name="to-host-the-usercontrol"></a><span data-ttu-id="d3076-135">Pour héberger le UserControl</span><span class="sxs-lookup"><span data-stu-id="d3076-135">To host the UserControl</span></span>  
  
1.  <span data-ttu-id="d3076-136">Dans le Concepteur Windows Forms, ouvrez Form1.</span><span class="sxs-lookup"><span data-stu-id="d3076-136">In the Windows Forms Designer, open Form1.</span></span>  
  
2.  <span data-ttu-id="d3076-137">Dans la fenêtre Propriétés, cliquez sur **événements**, puis double-cliquez sur le <xref:System.Windows.Forms.Form.Load> événement pour créer un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d3076-137">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>  
  
     <span data-ttu-id="d3076-138">Ouvre l’éditeur de Code généré récemment `Form1_Load` Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d3076-138">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>  
  
3.  <span data-ttu-id="d3076-139">Remplacez le code dans Form1.cs par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d3076-139">Replace the code in Form1.cs with the following code.</span></span>  
  
     <span data-ttu-id="d3076-140">Le `Form1_Load` Gestionnaire d’événements crée une instance de `UserControl1` et ajoute ses paramètres le <xref:System.Windows.Forms.Integration.ElementHost> collection de contrôles enfants du contrôle.</span><span class="sxs-lookup"><span data-stu-id="d3076-140">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="d3076-141">Le <xref:System.Windows.Forms.Integration.ElementHost> contrôle est ajouté à la collection du formulaire des contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="d3076-141">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="d3076-142">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d3076-142">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3076-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3076-143">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="d3076-144">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="d3076-144">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="d3076-145">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3076-145">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="d3076-146">Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="d3076-146">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="d3076-147">Hébergement d’un contrôle Composite WPF dans les Windows Forms, exemple</span><span class="sxs-lookup"><span data-stu-id="d3076-147">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160001)
