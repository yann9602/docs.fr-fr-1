---
title: "Comment&#160;: cr&#233;er un compl&#233;ment qui retourne une interface utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "complément (WPF), retourne une interface utilisateur"
  - "créer un complément qui retourne une interface utilisateur (WPF)"
  - "implémenter des segments de pipeline de complément (WPF)"
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: cr&#233;er un compl&#233;ment qui retourne une interface utilisateur
Cet exemple montre comment créer un complément qui retourne une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] à une application autonome [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hôte.  
  
 Le complément retourne une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui correspond à un contrôle utilisateur [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Le contenu du contrôle utilisateur est un bouton unique qui, lorsque vous cliquez dessus, affiche un message.  L'application autonome [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] héberge le complément et affiche le contrôle utilisateur \(retourné par le complément\) en tant que contenu de la fenêtre d'application principale.  
  
 **Composants requis**  
  
 Cet exemple met en surbrillance les extensions [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] au modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] qui activent ce scénario et suppose ce qui suit :  
  
-   Connaissance du modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], y compris du développement du pipeline, du complément et de l'hôte.  Si ces concepts ne vous sont pas familiers, consultez [Compléments et extensibilité](../../../../ml/index.xml).  Pour obtenir des instructions pas à pas pour l'implémentation d'un pipeline, d'un complément et d'une application hôte, consultez [Procédure pas à pas : création d'une application extensible](../Topic/Walkthrough:%20Creating%20an%20Extensible%20Application.md).  
  
-   Connaissance des extensions [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] au modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], que vous pouvez trouver dans : [Vue d'ensemble des compléments WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
## Exemple  
 La création d'un complément qui retourne une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] requiert un code spécifique pour chaque segment de pipeline, le complément et l'application hôte.  
  
   
  
<a name="Contract"></a>   
## Implémentation du segment de pipeline du contrat  
 Une méthode doit être définie par le contrat pour retourner une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] et sa valeur de retour doit être de type <xref:System.AddIn.Contract.INativeHandleContract>.  La méthode `GetAddInUI` du contrat `IWPFAddInContract` utilisée dans le code suivant montre comment procéder.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## Implémentation du segment de pipeline de la vue du complément  
 Comme le complément implémente les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] qu'il fournit comme sous\-classes de <xref:System.Windows.FrameworkElement>, la méthode utilisée dans la vue du complément qui correspond à `IWPFAddInView.GetAddInUI` doit retourner une valeur de type <xref:System.Windows.FrameworkElement>.  Le code suivant affiche la vue du complément du contrat, implémentée sous forme d'interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## Implémentation du segment d'adaptateur côté complément du pipeline  
 La méthode du contrat retourne un <xref:System.AddIn.Contract.INativeHandleContract>, tandis que le complément retourne un <xref:System.Windows.FrameworkElement> \(comme défini dans la vue du complément\).  Par conséquent, le <xref:System.Windows.FrameworkElement> doit être converti en un <xref:System.AddIn.Contract.INativeHandleContract> avant de passer par la limite d'isolation.  Cette opération est exécutée par l'adaptateur côté complément en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, comme indiqué dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## Implémentation du segment de pipeline de la vue hôte  
 Comme l'application hôte affiche un <xref:System.Windows.FrameworkElement>, la méthode dans la vue hôte qui correspond à `IWPFAddInHostView.GetAddInUI` doit retourner une valeur de type <xref:System.Windows.FrameworkElement>.  Le code suivant affiche la vue hôte du contrat, implémentée sous forme d'interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## Implémentation du segment d'adaptateur côté hôte du pipeline  
 La méthode du contrat retourne un <xref:System.AddIn.Contract.INativeHandleContract>, alors que l'application hôte attend un <xref:System.Windows.FrameworkElement> \(comme spécifié par la vue hôte\).  Par conséquent, le <xref:System.AddIn.Contract.INativeHandleContract> doit être converti en un <xref:System.Windows.FrameworkElement> après être passé par la limite d'isolation.  Cette opération est exécutée par l'adaptateur côté hôte en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, comme illustré dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## Implémentation du complément  
 Une fois l'adaptateur côté complément et la vue du complément créés, le complément \(`WPFAddIn1.AddIn`\) doit implémenter la méthode `IWPFAddInView.GetAddInUI` pour retourner un objet <xref:System.Windows.FrameworkElement> \(un <xref:System.Windows.Controls.UserControl> dans cet exemple\).  L'implémentation du <xref:System.Windows.Controls.UserControl>, `AddInUI`, est illustrée par le code suivant.  
  
 [!code-xml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 L'implémentation de `IWPFAddInView.GetAddInUI` par le complément doit simplement retourner une nouvelle instance de `AddInUI`, comme illustré par le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## Implémentation de l'application hôte  
 Une fois l'adaptateur côté hôte et la vue hôte créés, l'application hôte peut utiliser le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour ouvrir le pipeline, acquérir une vue hôte du complément et appeler la méthode `IWPFAddInHostView.GetAddInUI`.  Ces étapes sont illustrées dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## Voir aussi  
 [Compléments et extensibilité](../../../../ml/index.xml)   
 [Vue d'ensemble des compléments WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)