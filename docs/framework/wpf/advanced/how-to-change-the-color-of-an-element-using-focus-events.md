---
title: "Comment&#160;: modifier la couleur d&#39;un &#233;l&#233;ment &#224; l&#39;aide d&#39;&#233;v&#233;nements Focus | Microsoft Docs"
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
  - "couleurs des éléments, modifier"
  - "éléments, changer la couleur"
  - "événements de focus, changer la couleur des éléments pour"
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: modifier la couleur d&#39;un &#233;l&#233;ment &#224; l&#39;aide d&#39;&#233;v&#233;nements Focus
Cet exemple montre comment modifier la couleur d'un élément lorsqu'il obtient et perd le focus à l'aide des événements <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus>.  
  
 Cet exemple comprend un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et un fichier code\-behind.  
  
## Exemple  
 Le code [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] suivant crée l'interface utilisateur, que se compose de deux objets <xref:System.Windows.Controls.Button> et attache des gestionnaires d'événements pour les événements <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus> aux objets <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Le code\-behind suivant crée les gestionnaires d'événements <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus>.  Lorsque le <xref:System.Windows.Controls.Button> obtient le focus clavier, l'<xref:System.Windows.Controls.Control.Background%2A> du <xref:System.Windows.Controls.Button> devient rouge.  Lorsque le <xref:System.Windows.Controls.Button> perd le focus clavier, l'<xref:System.Windows.Controls.Control.Background%2A> du <xref:System.Windows.Controls.Button> redevient blanc.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## Voir aussi  
 [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)