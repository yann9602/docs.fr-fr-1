---
title: "Comment&#160;: animer la position d&#39;un objet &#224; l&#39;aide de PointAnimation | Microsoft Docs"
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
  - "animation, PointAnimation"
  - "classes, PointAnimation"
  - "graphiques (WPF), animation"
  - "PointAnimation (classe)"
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: animer la position d&#39;un objet &#224; l&#39;aide de PointAnimation
Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.Animation.PointAnimation> pour animer un objet le long d'un <xref:System.Windows.Shapes.Path>.  
  
## Exemple  
 L'exemple suivant déplace une ellipse le long d'un <xref:System.Windows.Shapes.Path>, d'un point de l'écran à un autre.  L'exemple anime la position d'un <xref:System.Windows.Media.EllipseGeometry> en utilisant <xref:System.Windows.Media.Animation.PointAnimation> pour animer la propriété <xref:System.Windows.Media.EllipseGeometry.Center%2A>.  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.PointAnimation>   
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.EllipseGeometry>   
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Graphiques et multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)   
 [Animation and Timing](http://msdn.microsoft.com/fr-fr/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)