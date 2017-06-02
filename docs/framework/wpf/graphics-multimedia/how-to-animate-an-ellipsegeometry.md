---
title: "Comment&#160;: animer un EllipseGeometry | Microsoft Docs"
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
  - "animation, objets EllipseGeometry"
  - "Objets EllipseGeometry, animation"
  - "graphiques (WPF), animation"
ms.assetid: 767b9b6e-9cb7-482e-b6c2-fee7750c3995
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: animer un EllipseGeometry
Cet exemple montre comment animer une <xref:System.Windows.Media.Geometry> dans un <xref:System.Windows.Shapes.Path> élément. Dans l’exemple suivant, un <xref:System.Windows.Media.Animation.PointAnimation> est utilisé pour animer la <xref:System.Windows.Media.EllipseGeometry.Center%2A> d’un <xref:System.Windows.Media.EllipseGeometry>.  
  
## <a name="example"></a>Exemple  
 [!code-xml[animatepath_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip_XAML/CS/EllipseGeometryExample.xaml#1)]  
  
 [!code-csharp[animatepath_snip#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip/CSharp/EllipseGeometryExample.cs#101)]  
  
 [!code-vb[animatepath_snip#201](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animatepath_snip/VisualBasic/EllipseGeometryExample.vb#201)]  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)