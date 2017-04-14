---
title: "Comment&#160;: cr&#233;er un Expander avec un ScrollViewer | Microsoft Docs"
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
  - "contrôles (WPF), Expander"
  - "contrôles (WPF), ScrollViewer"
  - "Expander (contrôle), créer"
  - "ScrollViewer (contrôle), avec un contrôle Expander"
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: cr&#233;er un Expander avec un ScrollViewer
Cet exemple montre comment créer un contrôle <xref:System.Windows.Controls.Expander> avec un contenu complexe comme une image ou du texte.  L'exemple joint également le contenu du <xref:System.Windows.Controls.Expander> dans un contrôle <xref:System.Windows.Controls.ScrollViewer>.  
  
## Exemple  
 L'exemple suivant montre comment créer un <xref:System.Windows.Controls.Expander>.  L'exemple utilise un contrôle <xref:System.Windows.Controls.Primitives.BulletDecorator>, qui contient une image et du texte, afin de définir le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.  Un contrôle <xref:System.Windows.Controls.ScrollViewer> fournit une méthode pour faire défiler le contenu développé.  
  
 Notez que l'exemple définit la propriété <xref:System.Windows.FrameworkElement.Height%2A> sur le <xref:System.Windows.Controls.ScrollViewer> et non pas sur le contenu.  Si le <xref:System.Windows.FrameworkElement.Height%2A> est défini sur le contenu, le <xref:System.Windows.Controls.ScrollViewer> ne permet pas à l'utilisateur de faire défiler le contenu.  La propriété <xref:System.Windows.FrameworkElement.Width%2A> est définie sur le contrôle <xref:System.Windows.Controls.Expander> et ce paramètre s'applique au <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et au contenu développé.  
  
 [!code-xml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Expander>   
 [Vue d'ensemble de l'expanseur](../../../../docs/framework/wpf/controls/expander-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)