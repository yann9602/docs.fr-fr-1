---
title: "Comment&#160;: mettre un &#233;l&#233;ment en rotation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "classes, DoubleAnimation"
  - "classes, RotateTransform"
  - "DoubleAnimation (classe)"
  - "graphiques, faire pivoter des éléments"
  - "RotateTransform (classe)"
  - "faire pivoter des éléments"
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: mettre un &#233;l&#233;ment en rotation
Cet exemple montre comment mettre un élément en rotation à l'aide d'un <xref:System.Windows.Media.RotateTransform> et d'un <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 L'exemple suivant applique le <xref:System.Windows.Media.RotateTransform> à la propriété <xref:System.Windows.UIElement.RenderTransform%2A> de l'élément.  L'exemple utilise un <xref:System.Windows.Media.Animation.DoubleAnimation> pour animer l'<xref:System.Windows.Media.RotateTransform.Angle%2A> du <xref:System.Windows.Media.RotateTransform>.  Pour mettre un élément en rotation, l'exemple définit la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> de l'élément sur le point \(0.5, 0.5\).  
  
## Exemple  
 [!code-xml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Pour obtenir l'exemple complet, qui inclut des exemples de transformation supplémentaires, consultez [Transformations 2D, exemple](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)