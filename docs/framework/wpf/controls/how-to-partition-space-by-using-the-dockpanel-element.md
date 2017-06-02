---
title: "Comment&#160;: partitionner l&#39;espace &#224; l&#39;aide de l&#39;&#233;l&#233;ment DockPanel | Microsoft Docs"
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
  - "contrôles (WPF), DockPanel"
  - "DockPanel (contrôle), partitionner l'espace"
  - "partitionner l'espace"
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: partitionner l&#39;espace &#224; l&#39;aide de l&#39;&#233;l&#233;ment DockPanel
L'exemple suivant crée une infrastructure d'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] simple à l'aide d'un élément <xref:System.Windows.Controls.DockPanel>.  Le <xref:System.Windows.Controls.DockPanel> partitionne l'espace disponible pour ses éléments enfants.  
  
## Exemple  
 Cet exemple utilise la propriété <xref:System.Windows.Controls.DockPanel.Dock%2A>, qui est une [propriété attachée](GTMT), pour ancrer deux éléments <xref:System.Windows.Controls.Border> identiques en <xref:System.Windows.Controls.Dock> de l'espace partitionné.  Un troisième élément <xref:System.Windows.Controls.Border> est ancré au <xref:System.Windows.Controls.Dock>, sa largeur ayant une valeur de 200 pixels.  Un quatrième <xref:System.Windows.Controls.Border> est ancré au <xref:System.Windows.Controls.Dock> de l'écran.  Le dernier élément <xref:System.Windows.Controls.Border> remplit automatiquement l'espace restant.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Par défaut, le dernier enfant d'un élément <xref:System.Windows.Controls.DockPanel> remplit l'espace non alloué restant.  Si ce comportement ne vous convient pas, définissez `LastChildFill="False"`.  
  
 L'application compilée produit une nouvelle interface utilisateur semblable à ce qui suit.  
  
 ![Scénario DockPanel classique.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.png "panel\_intro\_dockpanel")  
  
## Voir aussi  
 <xref:System.Windows.Controls.DockPanel>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)