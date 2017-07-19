---
title: "Comment&#160;: appliquer des propri&#233;t&#233;s Stretch au contenu d&#39;un Viewbox | Microsoft Docs"
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
  - "contrôles, Viewbox"
  - "propriétés Stretch"
  - "propriétés StretchDirection"
  - "Viewbox (contrôle)"
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: appliquer des propri&#233;t&#233;s Stretch au contenu d&#39;un Viewbox
## Exemple  
 Cet exemple indique comment modifier la valeur des propriétés <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> et <xref:System.Windows.Controls.Viewbox.Stretch%2A> d'un <xref:System.Windows.Controls.Viewbox>.  
  
 Le premier exemple utilise [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour définir un élément <xref:System.Windows.Controls.Viewbox>.  Il assigne un <xref:System.Windows.FrameworkElement.MaxWidth%2A> et un <xref:System.Windows.FrameworkElement.MaxHeight%2A> de 400.  L'exemple imbrique un élément <xref:System.Windows.Controls.Image> dans le <xref:System.Windows.Controls.Viewbox>.  Les éléments <xref:System.Windows.Controls.Button> qui correspondent aux valeurs de propriété des énumérations <xref:System.Windows.Controls.Viewbox.Stretch%2A> et <xref:System.Windows.Controls.StretchDirection> manipulent le comportement d'étirement du <xref:System.Windows.Controls.Image> imbriqué.  
  
 [!code-xml[viewboxStretchLayoutSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 Le fichier code\-behind suivant gère les événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du <xref:System.Windows.Controls.Button> définis dans l'exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Viewbox>   
 <xref:System.Windows.Media.Stretch>   
 <xref:System.Windows.Controls.StretchDirection>