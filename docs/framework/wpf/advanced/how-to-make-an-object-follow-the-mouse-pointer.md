---
title: "Comment&#160;: faire en sorte qu&#39;un objet suive le pointeur de la souris | Microsoft Docs"
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
  - "curseur (pointeur de la souris), faire suivre des objets"
  - "suivre le pointeur de la souris (curseur)"
  - "pointeur de la souris (curseur), faire suivre des objets"
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: faire en sorte qu&#39;un objet suive le pointeur de la souris
Cet exemple montre comment modifier les dimensions d'un objet lorsque le pointeur de la souris se déplace à l'écran.  
  
 L'exemple inclut un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui crée le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] et un fichier code\-behind qui crée le gestionnaire d'événements.  
  
## Exemple  
 Le code [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] suivant crée l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui se compose d'un <xref:System.Windows.Shapes.Ellipse> dans un <xref:System.Windows.Controls.StackPanel> et joint le gestionnaire d'événements pour l'événement <xref:System.Windows.UIElement.MouseMove>.  
  
 [!code-xml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Le code\-behind suivant crée le gestionnaire d'événements <xref:System.Windows.UIElement.MouseMove>.  Lorsque le pointeur de la souris déplace, la hauteur et la largeur de <xref:System.Windows.Shapes.Ellipse> augmentent et diminuent.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## Voir aussi  
 [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)