---
title: "Procédure pas à pas : hébergement d'un contrôle Windows Forms dans WPF"
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
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce6920e8a6cea08f4aba083b99d56b4252409827
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="f722c-102">Procédure pas à pas : hébergement d'un contrôle Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="f722c-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="f722c-103"> fournit de nombreux contrôles avec un ensemble complet de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="f722c-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="f722c-104">Toutefois, vous souhaiterez parfois utiliser [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle sur votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span><span class="sxs-lookup"><span data-stu-id="f722c-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="f722c-105">Par exemple, avoir un investissement substantiel existant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles, ou vous pouvez avoir un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle qui fournit des fonctionnalités uniques.</span><span class="sxs-lookup"><span data-stu-id="f722c-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="f722c-106">Cette procédure pas à pas vous montre comment héberger un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control sur un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="f722c-106">This walkthrough shows you how to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>  
  
 <span data-ttu-id="f722c-107">Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [qui héberge un contrôle Windows Forms dans WPF, exemple](http://go.microsoft.com/fwlink/?LinkID=160057).</span><span class="sxs-lookup"><span data-stu-id="f722c-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=160057).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f722c-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f722c-108">Prerequisites</span></span>  
 <span data-ttu-id="f722c-109">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="f722c-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="f722c-110">.</span><span class="sxs-lookup"><span data-stu-id="f722c-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="f722c-111">Hébergement d’un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f722c-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="f722c-112">Pour héberger le contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="f722c-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="f722c-113">Créez un projet d’Application WPF nommé `HostingWfInWpf`.</span><span class="sxs-lookup"><span data-stu-id="f722c-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>  
  
2.  <span data-ttu-id="f722c-114">Ajoutez les références aux assemblys suivants.</span><span class="sxs-lookup"><span data-stu-id="f722c-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="f722c-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="f722c-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="f722c-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="f722c-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="f722c-117">Ouvrez MainWindow.xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f722c-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="f722c-118">Nom de la <xref:System.Windows.Controls.Grid> élément `grid1`.</span><span class="sxs-lookup"><span data-stu-id="f722c-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  <span data-ttu-id="f722c-119">En mode Création ou la vue XAML, sélectionnez le <xref:System.Windows.Window> élément.</span><span class="sxs-lookup"><span data-stu-id="f722c-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="f722c-120">Dans la fenêtre Propriétés, cliquez sur le **événements** onglet.</span><span class="sxs-lookup"><span data-stu-id="f722c-120">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="f722c-121">Double-cliquez sur le <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="f722c-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="f722c-122">Insérez le code suivant pour gérer les <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="f722c-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. <span data-ttu-id="f722c-123">En haut du fichier, ajoutez le code suivant `Imports` ou `using` instruction.</span><span class="sxs-lookup"><span data-stu-id="f722c-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. <span data-ttu-id="f722c-124">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="f722c-124">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f722c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f722c-125">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="f722c-126">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="f722c-126">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="f722c-127">Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF avec XAML</span><span class="sxs-lookup"><span data-stu-id="f722c-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [<span data-ttu-id="f722c-128">Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="f722c-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="f722c-129">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f722c-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="f722c-130">Contrôles Windows Forms et contrôles WPF équivalents</span><span class="sxs-lookup"><span data-stu-id="f722c-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="f722c-131">Hébergement d’un contrôle Windows Forms dans WPF, exemple</span><span class="sxs-lookup"><span data-stu-id="f722c-131">Hosting a Windows Forms Control in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160057)
