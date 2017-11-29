---
title: "Comment : créer un complément qui retourne une interface utilisateur"
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
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd6956f1934f8594a941b57066cc2d4d6214a9a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="29ea5-102">Comment : créer un complément qui retourne une interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="29ea5-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="29ea5-103">Cet exemple montre comment créer un complément qui retourne un [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] vers un ordinateur hôte [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application autonome.</span><span class="sxs-lookup"><span data-stu-id="29ea5-103">This example shows how to create an add-in that returns a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)][!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to a host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application.</span></span>  
  
 <span data-ttu-id="29ea5-104">Le complément retourne un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui est un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="29ea5-104">The add-in returns a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that is a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] user control.</span></span> <span data-ttu-id="29ea5-105">Le contenu du contrôle utilisateur est un bouton unique qui, quand on clique dessus, affiche une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="29ea5-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="29ea5-106">Le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application autonome héberge le complément et affiche le contrôle utilisateur (retourné par le complément) en tant que le contenu de la fenêtre principale de l’application.</span><span class="sxs-lookup"><span data-stu-id="29ea5-106">The [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="29ea5-107">**Composants requis**</span><span class="sxs-lookup"><span data-stu-id="29ea5-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="29ea5-108">Cet exemple met en évidence le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions pour le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modèle complément qui permet ce scénario et suppose ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="29ea5-108">This example highlights the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="29ea5-109">Connaissance de la [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] complément modèle, y compris le pipeline de complément et développement de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="29ea5-109">Knowledge of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="29ea5-110">Si vous n’êtes pas familiarisé avec ces concepts, consultez [des compléments et extensibilité](../../../../docs/framework/add-ins/index.md).</span><span class="sxs-lookup"><span data-stu-id="29ea5-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](../../../../docs/framework/add-ins/index.md).</span></span> <span data-ttu-id="29ea5-111">Pour obtenir un didacticiel qui montre l’implémentation d’un pipeline, d’un complément et d’une application hôte, consultez [procédure pas à pas : création d’une Application Extensible](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="29ea5-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="29ea5-112">Connaissance de la [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions pour le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] -modèle de complément, qui se trouve ici : [vue d’ensemble des compléments WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="29ea5-112">Knowledge of the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29ea5-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="29ea5-113">Example</span></span>  
 <span data-ttu-id="29ea5-114">Pour créer un complément qui retourne un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requiert un code spécifique pour chaque segment de pipeline, le complément et l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="29ea5-114">To create an add-in that returns a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="29ea5-115">Implémentation du segment de pipeline de contrat</span><span class="sxs-lookup"><span data-stu-id="29ea5-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="29ea5-116">Une méthode doit être définie par le contrat pour retourner un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], et sa valeur de retour doit être de type <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="29ea5-116">A method must be defined by the contract for returning a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="29ea5-117">Cela est illustré par le `GetAddInUI` méthode de la `IWPFAddInContract` de contrat dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29ea5-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="29ea5-118">Implémentation du segment de pipeline de vue de complément</span><span class="sxs-lookup"><span data-stu-id="29ea5-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="29ea5-119">Étant donné que le complément implémente la [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] il fournit comme sous-classes de <xref:System.Windows.FrameworkElement>, la méthode sur la vue qui correspond à `IWPFAddInView.GetAddInUI` doit retourner une valeur de type <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="29ea5-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="29ea5-120">Le code suivant illustre la vue de complément du contrat, implémentée en tant qu’interface.</span><span class="sxs-lookup"><span data-stu-id="29ea5-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="29ea5-121">Implémentation du segment de pipeline d’adaptateur côté complément</span><span class="sxs-lookup"><span data-stu-id="29ea5-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="29ea5-122">La méthode du contrat retourne un <xref:System.AddIn.Contract.INativeHandleContract>, mais le complément retourne un <xref:System.Windows.FrameworkElement> (comme spécifié par la vue du complément).</span><span class="sxs-lookup"><span data-stu-id="29ea5-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="29ea5-123">Par conséquent, le <xref:System.Windows.FrameworkElement> doit être converti en un <xref:System.AddIn.Contract.INativeHandleContract> avant de passer par la limite d’isolation.</span><span class="sxs-lookup"><span data-stu-id="29ea5-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="29ea5-124">Cette opération est exécutée par l’adaptateur côté complément en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29ea5-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="29ea5-125">Implémentation du segment de pipeline de vue hôte</span><span class="sxs-lookup"><span data-stu-id="29ea5-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="29ea5-126">Étant donné que l’application hôte affiche un <xref:System.Windows.FrameworkElement>, la méthode sur la vue hôte qui correspond à `IWPFAddInHostView.GetAddInUI` doit retourner une valeur de type <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="29ea5-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="29ea5-127">Le code suivant illustre la vue hôte du contrat, implémentée en tant qu’interface.</span><span class="sxs-lookup"><span data-stu-id="29ea5-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="29ea5-128">Implémentation du segment de pipeline d’adaptateur côté hôte</span><span class="sxs-lookup"><span data-stu-id="29ea5-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="29ea5-129">La méthode du contrat retourne un <xref:System.AddIn.Contract.INativeHandleContract>, mais l’application hôte attend un <xref:System.Windows.FrameworkElement> (comme spécifié par la vue hôte).</span><span class="sxs-lookup"><span data-stu-id="29ea5-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="29ea5-130">Par conséquent, le <xref:System.AddIn.Contract.INativeHandleContract> doit être converti en un <xref:System.Windows.FrameworkElement> après être passé par la limite d’isolation.</span><span class="sxs-lookup"><span data-stu-id="29ea5-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="29ea5-131">Cette opération est exécutée par l’adaptateur côté hôte en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29ea5-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="29ea5-132">Implémentation du complément</span><span class="sxs-lookup"><span data-stu-id="29ea5-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="29ea5-133">Avec l’adaptateur côté complément et la vue complément créé, le complément (`WPFAddIn1.AddIn`) doit implémenter la `IWPFAddInView.GetAddInUI` méthode pour retourner un <xref:System.Windows.FrameworkElement> objet (un <xref:System.Windows.Controls.UserControl> dans cet exemple).</span><span class="sxs-lookup"><span data-stu-id="29ea5-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="29ea5-134">L’implémentation de la <xref:System.Windows.Controls.UserControl>, `AddInUI`, est indiqué par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29ea5-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="29ea5-135">L’implémentation de la `IWPFAddInView.GetAddInUI` par le complément doit simplement retourner une nouvelle instance de `AddInUI`, comme indiqué par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29ea5-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="29ea5-136">Implémentation de l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="29ea5-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="29ea5-137">Avec l’adaptateur côté hôte et la vue hôte créés, l’application hôte peut utiliser le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modèle de complément pour ouvrir le pipeline, acquérir une vue hôte du complément et appelez le `IWPFAddInHostView.GetAddInUI` (méthode).</span><span class="sxs-lookup"><span data-stu-id="29ea5-137">With the host-side adapter and host view created, the host application can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="29ea5-138">Ces étapes sont présentées dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="29ea5-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="29ea5-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29ea5-139">See Also</span></span>  
 [<span data-ttu-id="29ea5-140">Compléments et extensibilité</span><span class="sxs-lookup"><span data-stu-id="29ea5-140">Add-ins and Extensibility</span></span>](../../../../docs/framework/add-ins/index.md)  
 [<span data-ttu-id="29ea5-141">Vue d’ensemble des compléments WPF</span><span class="sxs-lookup"><span data-stu-id="29ea5-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
