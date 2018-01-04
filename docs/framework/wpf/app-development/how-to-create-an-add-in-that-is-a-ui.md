---
title: "Guide pratique pour créer un complément qui est une interface utilisateur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fea1c718eedb12d49eced9964e4f9045badf07ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Guide pratique pour créer un complément qui est une interface utilisateur
Cet exemple montre comment créer un complément qui est une [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] qui est hébergé par un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application autonome.  
  
 Le complément est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui est un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] contrôle utilisateur. Le contenu du contrôle utilisateur est un bouton unique qui, quand on clique dessus, affiche une boîte de message. Le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application autonome héberge le complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] en tant que le contenu de la fenêtre principale de l’application.  
  
 **Composants requis**  
  
 Cet exemple met en évidence le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions pour le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modèle complément qui permet ce scénario et suppose ce qui suit :  
  
-   Connaissance de la [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] complément modèle, y compris le pipeline de complément et développement de l’hôte. Si vous n’êtes pas familiarisé avec ces concepts, consultez [des compléments et extensibilité](../../../../docs/framework/add-ins/index.md). Pour obtenir un didacticiel qui montre l’implémentation d’un pipeline, d’un complément et d’une application hôte, consultez [procédure pas à pas : création d’une Application Extensible](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).  
  
-   Connaissance de la [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions pour le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] -modèle de complément, qui se trouve ici : [vue d’ensemble des compléments WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemple  
 Pour créer un complément qui est une [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requiert un code spécifique pour chaque segment de pipeline, le complément et l’application hôte.  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implémentation du segment de pipeline de contrat  
 Lorsqu’un complément est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], le contrat pour le complément doit implémenter <xref:System.AddIn.Contract.INativeHandleContract>. Dans l’exemple, `IWPFAddInContract` implémente <xref:System.AddIn.Contract.INativeHandleContract>, comme illustré dans le code suivant.  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue de complément  
 Étant donné que le complément est implémenté comme une sous-classe de la <xref:System.Windows.FrameworkElement> type, la vue du complément doit également sous-classer <xref:System.Windows.FrameworkElement>. Le code suivant illustre la vue du complément du contrat, implémentée comme la `WPFAddInView` classe.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 Ici, la vue du complément est dérivée de <xref:System.Windows.Controls.UserControl>. Par conséquent, le complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] doit également dériver <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté complément  
 Alors que le contrat est un <xref:System.AddIn.Contract.INativeHandleContract>, le complément est une <xref:System.Windows.FrameworkElement> (comme spécifié par le segment de pipeline de complément vue). Par conséquent, le <xref:System.Windows.FrameworkElement> doit être converti en un <xref:System.AddIn.Contract.INativeHandleContract> avant de passer par la limite d’isolation. Cette opération est exécutée par l’adaptateur côté complément en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, comme illustré dans le code suivant.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 Dans le modèle de complément, où un complément retourne un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (consultez [créer un complément que retourne une interface utilisateur](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md)), converti de l’adaptateur de complément le <xref:System.Windows.FrameworkElement> à un <xref:System.AddIn.Contract.INativeHandleContract> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>doit également être appelé dans ce modèle, bien que vous devez implémenter une méthode à partir de laquelle écrire le code pour l’appeler. Pour cela, substituez <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> et implémentez le code qui appelle <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> si le code qui appelle <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> attend un <xref:System.AddIn.Contract.INativeHandleContract>. Dans ce cas, l’appelant sera l’adaptateur côté hôte, ce qui est traité dans une sous-section ultérieure.  
  
> [!NOTE]
>  Vous devez également remplacer <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> dans ce modèle pour activer la tabulation entre l’application hôte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] et complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Pour plus d’informations, consultez « Limitations des compléments WPF » dans [vue d’ensemble des compléments WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Étant donné que l’adaptateur côté complément implémente une interface qui dérive de <xref:System.AddIn.Contract.INativeHandleContract>, vous devez également implémenter <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, bien que cela est ignoré lorsque <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> est remplacée.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue hôte  
 Dans ce modèle, l’application hôte attend en général, l’affichage de l’ordinateur hôte doit être un <xref:System.Windows.FrameworkElement> sous-classe. L’adaptateur côté hôte doit convertir le <xref:System.AddIn.Contract.INativeHandleContract> à un <xref:System.Windows.FrameworkElement> après le <xref:System.AddIn.Contract.INativeHandleContract> dépasse la limite d’isolation. Car une méthode n’est pas appelée par l’application hôte pour obtenir le <xref:System.Windows.FrameworkElement>, la vue hôte doit « retourner » le <xref:System.Windows.FrameworkElement> par qui le contient. Par conséquent, la vue hôte doit dériver d’une sous-classe de <xref:System.Windows.FrameworkElement> qui peut contenir d’autres [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], tel que <xref:System.Windows.Controls.UserControl>. Le code suivant montre la vue hôte du contrat, implémentée comme la `WPFAddInHostView` classe.  
  
  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté hôte  
 Alors que le contrat est un <xref:System.AddIn.Contract.INativeHandleContract>, l’application hôte attend un <xref:System.Windows.Controls.UserControl> (comme spécifié par la vue hôte). Par conséquent, le <xref:System.AddIn.Contract.INativeHandleContract> doit être converti en un <xref:System.Windows.FrameworkElement> après être passé par la limite d’isolation, avant d’être définie en tant que contenu de la vue hôte (qui en dérive <xref:System.Windows.Controls.UserControl>).  
  
 Cette opération est exécutée par l’adaptateur côté hôte, comme illustré dans le code suivant.  
  
  
  
 Comme vous pouvez le voir, l’adaptateur côté hôte acquiert le <xref:System.AddIn.Contract.INativeHandleContract> en appelant l’adaptateur côté complément <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> (méthode) (il s’agit du point où la <xref:System.AddIn.Contract.INativeHandleContract> dépasse la limite d’isolation).  
  
 L’adaptateur côté hôte convertit ensuite le <xref:System.AddIn.Contract.INativeHandleContract> à un <xref:System.Windows.FrameworkElement> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Enfin, le <xref:System.Windows.FrameworkElement> est défini comme le contenu de la vue de l’hôte.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implémentation du complément  
 Avec l’adaptateur côté complément et la vue de complément en place, le complément peut être implémenté par dérivation de la vue de complément, comme illustré dans le code suivant.  
  
  
  
  
  
 Dans cet exemple, vous pouvez voir un avantage intéressant de ce modèle : complément, les développeurs doivent uniquement implémenter le complément (puisqu’il s’agit du [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] également), au lieu d’une classe, un complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>Implémentation de l'application hôte.  
 Avec l’adaptateur côté hôte et la vue hôte créés, l’application hôte peut utiliser le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modèle de complément pour ouvrir le pipeline et acquérir une vue hôte du complément. Ces étapes sont présentées dans le code suivant.  
  
  
  
 L’application hôte utilise classique [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] code du modèle de complément pour activer le complément, ce qui implicitement retourne la vue hôte à l’application hôte. L’application hôte affiche ensuite la vue de l’hôte (c'est-à-dire un <xref:System.Windows.Controls.UserControl>) à partir d’un <xref:System.Windows.Controls.Grid>.  
  
 Le code pour le traitement des interactions avec le complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] s’exécute dans domaine d’application du complément. Ces interactions incluent :  
  
-   Gère la <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.  
  
-   Indiquant le <xref:System.Windows.MessageBox>.  
  
 Cette activité est complètement isolée de l’application hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Compléments et extensibilité](../../../../docs/framework/add-ins/index.md)  
 [Vue d’ensemble des compléments WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
