---
title: "Procédure pas à pas : hébergement d'un contrôle ActiveX dans WPF"
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
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0e85c715db30c6e577980376d25d56238e2835a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="71f1d-102">Procédure pas à pas : hébergement d'un contrôle ActiveX dans WPF</span><span class="sxs-lookup"><span data-stu-id="71f1d-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="71f1d-103">Pour permettre une interaction améliorée avec les navigateurs, vous pouvez utiliser [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] des contrôles dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur.</span><span class="sxs-lookup"><span data-stu-id="71f1d-103">To enable improved interaction with browsers, you can use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="71f1d-104">Cette procédure pas à pas montre comment vous pouvez héberger le [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] comme un contrôle sur un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span><span class="sxs-lookup"><span data-stu-id="71f1d-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>  
  
 <span data-ttu-id="71f1d-105">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="71f1d-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="71f1d-106">Création du projet</span><span class="sxs-lookup"><span data-stu-id="71f1d-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="71f1d-107">Création du contrôle ActiveX.</span><span class="sxs-lookup"><span data-stu-id="71f1d-107">Creating the ActiveX control.</span></span>  
  
-   <span data-ttu-id="71f1d-108">Hébergement du contrôle ActiveX sur une Page WPF.</span><span class="sxs-lookup"><span data-stu-id="71f1d-108">Hosting the ActiveX control on a WPF Page.</span></span>  
  
 <span data-ttu-id="71f1d-109">Lorsque vous avez terminé cette procédure pas à pas, vous saurez comment utiliser [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] des contrôles dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur.</span><span class="sxs-lookup"><span data-stu-id="71f1d-109">When you have completed this walkthrough, you will understand how to use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="71f1d-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="71f1d-110">Prerequisites</span></span>  
 <span data-ttu-id="71f1d-111">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="71f1d-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]<span data-ttu-id="71f1d-112">installé sur l’ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.</span><span class="sxs-lookup"><span data-stu-id="71f1d-112"> installed on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="71f1d-113">.</span><span class="sxs-lookup"><span data-stu-id="71f1d-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="71f1d-114">Création du projet</span><span class="sxs-lookup"><span data-stu-id="71f1d-114">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="71f1d-115">Pour créer et configurer le projet</span><span class="sxs-lookup"><span data-stu-id="71f1d-115">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="71f1d-116">Créez un projet d’Application WPF nommé `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="71f1d-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>  
  
2.  <span data-ttu-id="71f1d-117">Ajouter un projet de bibliothèque de contrôles Windows Forms à la solution et nommez le projet `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="71f1d-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>  
  
3.  <span data-ttu-id="71f1d-118">Dans le projet WmpAxLib, ajoutez une référence à l’assembly de lecteur Windows Media nommé wmp.dll.</span><span class="sxs-lookup"><span data-stu-id="71f1d-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>  
  
4.  <span data-ttu-id="71f1d-119">Ouvrez le **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="71f1d-119">Open the **Toolbox**.</span></span>  
  
5.  <span data-ttu-id="71f1d-120">Avec le bouton droit dans le **boîte à outils**, puis cliquez sur **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="71f1d-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>  
  
6.  <span data-ttu-id="71f1d-121">Cliquez sur le **des composants COM** onglet, sélectionnez le **le lecteur Windows Media** contrôler, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="71f1d-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>  
  
     <span data-ttu-id="71f1d-122">Le contrôle Windows Media Player est ajouté à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="71f1d-122">The Windows Media Player control is added to the **Toolbox**.</span></span>  
  
7.  <span data-ttu-id="71f1d-123">Dans l’Explorateur de solutions, cliquez sur le **UserControl1** de fichiers, puis cliquez sur **renommer**.</span><span class="sxs-lookup"><span data-stu-id="71f1d-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>  
  
8.  <span data-ttu-id="71f1d-124">Remplacez le nom par `WmpAxControl.vb` ou `WmpAxControl.cs`, selon le langage.</span><span class="sxs-lookup"><span data-stu-id="71f1d-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>  
  
9. <span data-ttu-id="71f1d-125">Si vous êtes invité à renommer toutes les références, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="71f1d-125">If you are prompted to rename all references, click **Yes**.</span></span>  
  
## <a name="creating-the-activex-control"></a><span data-ttu-id="71f1d-126">Création du contrôle ActiveX</span><span class="sxs-lookup"><span data-stu-id="71f1d-126">Creating the ActiveX Control</span></span>  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]<span data-ttu-id="71f1d-127">génère automatiquement un <xref:System.Windows.Forms.AxHost> classe wrapper pour un [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] contrôle lorsque le contrôle est ajouté à une aire de conception.</span><span class="sxs-lookup"><span data-stu-id="71f1d-127"> automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] control when the control is added to a design surface.</span></span> <span data-ttu-id="71f1d-128">La procédure suivante crée un assembly managé nommé AxInterop.WMPLib.dll.</span><span class="sxs-lookup"><span data-stu-id="71f1d-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>  
  
#### <a name="to-create-the-activex-control"></a><span data-ttu-id="71f1d-129">Pour créer le contrôle ActiveX</span><span class="sxs-lookup"><span data-stu-id="71f1d-129">To create the ActiveX control</span></span>  
  
1.  <span data-ttu-id="71f1d-130">Ouvrez WmpAxControl.cs ou WmpAxControl.vb dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="71f1d-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="71f1d-131">À partir de la **boîte à outils**, ajoutez le contrôle de lecteur Windows Media à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="71f1d-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>  
  
3.  <span data-ttu-id="71f1d-132">Dans la fenêtre Propriétés, définissez la valeur du contrôle Lecteur Windows Media <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="71f1d-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
4.  <span data-ttu-id="71f1d-133">Générez le projet de bibliothèque de contrôles WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="71f1d-133">Build the WmpAxLib control library project.</span></span>  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="71f1d-134">Hébergement du contrôle ActiveX sur une Page WPF</span><span class="sxs-lookup"><span data-stu-id="71f1d-134">Hosting the ActiveX Control on a WPF Page</span></span>  
  
#### <a name="to-host-the-activex-control"></a><span data-ttu-id="71f1d-135">Pour héberger le contrôle ActiveX</span><span class="sxs-lookup"><span data-stu-id="71f1d-135">To host the ActiveX control</span></span>  
  
1.  <span data-ttu-id="71f1d-136">Dans le projet HostingAxInWpf, ajoutez une référence à généré [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="71f1d-136">In the HostingAxInWpf project, add a reference to the generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperability assembly.</span></span>  
  
     <span data-ttu-id="71f1d-137">Cet assembly est nommé AxInterop.WMPLib.dll et a été ajouté au dossier Debug du projet WmpAxLib lorsque vous avez importé le contrôle du lecteur Windows Media.</span><span class="sxs-lookup"><span data-stu-id="71f1d-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>  
  
2.  <span data-ttu-id="71f1d-138">Ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="71f1d-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="71f1d-139">Ajoutez une référence à la [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly nommé System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="71f1d-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>  
  
4.  <span data-ttu-id="71f1d-140">Ouvrez MainWindow.xaml dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="71f1d-140">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
5.  <span data-ttu-id="71f1d-141">Nom de la <xref:System.Windows.Controls.Grid> élément `grid1`.</span><span class="sxs-lookup"><span data-stu-id="71f1d-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  <span data-ttu-id="71f1d-142">En mode Création ou la vue XAML, sélectionnez le <xref:System.Windows.Window> élément.</span><span class="sxs-lookup"><span data-stu-id="71f1d-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
7.  <span data-ttu-id="71f1d-143">Dans la fenêtre Propriétés, cliquez sur le **événements** onglet.</span><span class="sxs-lookup"><span data-stu-id="71f1d-143">In the Properties window, click the **Events** tab.</span></span>  
  
8.  <span data-ttu-id="71f1d-144">Double-cliquez sur le <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="71f1d-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
9. <span data-ttu-id="71f1d-145">Insérez le code suivant pour gérer les <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="71f1d-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     <span data-ttu-id="71f1d-146">Ce code crée une instance de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôler et ajoute une instance de la `AxWindowsMediaPlayer` contrôle enfant.</span><span class="sxs-lookup"><span data-stu-id="71f1d-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="71f1d-147">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="71f1d-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f1d-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71f1d-148">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="71f1d-149">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="71f1d-149">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="71f1d-150">Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="71f1d-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="71f1d-151">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71f1d-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
