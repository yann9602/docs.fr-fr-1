---
title: "Comment&#160;: animer un Popup | Microsoft Docs"
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
  - "animation, contrôles Popup"
  - "Popup (contrôle), animer"
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: animer un Popup
Cet exemple montre deux façons d'animer un contrôle <xref:System.Windows.Controls.Primitives.Popup>.  
  
## Exemple  
 L'exemple de code suivant affecte à la propriété <xref:System.Windows.Controls.Primitives.PopupAnimation> la valeur <xref:System.Windows.Controls.Primitives.PopupAnimation> qui provoque le « glissement » du <xref:System.Windows.Controls.Primitives.Popup> lorsqu'il apparaît.  
  
 Afin de faire pivoter le <xref:System.Windows.Controls.Primitives.Popup>, cet exemple affecte un <xref:System.Windows.Media.RotateTransform> à la propriété <xref:System.Windows.UIElement.RenderTransform%2A> de la <xref:System.Windows.Controls.Canvas>, qui est l'élément enfant du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Pour que la transformation fonctionne correctement, la propriété <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> de l'exemple doit avoir la valeur `true`.  En outre, la <xref:System.Windows.FrameworkElement.Margin%2A> du contenu de la <xref:System.Windows.Controls.Canvas> doit prévoir un espace suffisant pour permettre la rotation du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 L'exemple suivant montre comment un événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> qui se produit lors d'un clic sur le <xref:System.Windows.Controls.Button>, déclenche le <xref:System.Windows.Media.Animation.Storyboard> qui démarre l'animation.  
  
 [!code-xml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## Voir aussi  
 <xref:System.Windows.UIElement.RenderTransform%2A>   
 <xref:System.Windows.Controls.Primitives.BulletDecorator>   
 <xref:System.Windows.Media.RotateTransform>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 <xref:System.Windows.Controls.Primitives.Popup>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)   
 [Vue d'ensemble de Popup](../../../../docs/framework/wpf/controls/popup-overview.md)