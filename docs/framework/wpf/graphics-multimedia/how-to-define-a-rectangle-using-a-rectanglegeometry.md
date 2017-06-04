---
title: "Comment&#160;: d&#233;finir un rectangle &#224; l&#39;aide d&#39;un RectangleGeometry | Microsoft Docs"
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
  - "classes, RectangleGeometry"
  - "graphiques (WPF), rectangles"
  - "RectangleGeometry (classe)"
  - "rectangles, créer avec la classe RectangleGeometry"
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: d&#233;finir un rectangle &#224; l&#39;aide d&#39;un RectangleGeometry
Cet exemple décrit comment utiliser la classe <xref:System.Windows.Media.RectangleGeometry> pour décrire un rectangle.  
  
## Exemple  
 L'exemple suivant montre comment créer et rendre un <xref:System.Windows.Media.RectangleGeometry>.  La position relative et les dimensions du rectangle sont définies par une structure <xref:System.Windows.Rect>.  La position relative est `50,50`. La hauteur et la largeur sont toutes les deux de `25` et forment un carré.  L'intérieur du rectangle est peint avec un pinceau <xref:System.Windows.Media.Brushes.LemonChiffon%2A> et son plan est peint avec un trait <xref:System.Windows.Media.Brushes.Black%2A> d'une épaisseur de `1`.  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.png "graphicsmm\_rectangle")  
RectangleGeometry  
  
 Bien que cet exemple ait utilisé un élément <xref:System.Windows.Shapes.Path> pour restituer le <xref:System.Windows.Media.RectangleGeometry>, de nombreuses autres méthodes permettent d'utiliser des objets <xref:System.Windows.Media.RectangleGeometry>.  Par exemple, un <xref:System.Windows.Media.RectangleGeometry> peut être utilisé pour spécifier le <xref:System.Windows.UIElement.Clip%2A> d'un <xref:System.Windows.UIElement> ou le <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> d'un <xref:System.Windows.Media.GeometryDrawing>.  
  
 D'autres classes de géométrie simple incluent <xref:System.Windows.Media.LineGeometry> et <xref:System.Windows.Media.EllipseGeometry>.  Ces géométries, ainsi que d'autres plus complexes, peuvent également être créées à l'aide d'un <xref:System.Windows.Media.PathGeometry> ou d'un <xref:System.Windows.Media.StreamGeometry>.  
  
## Voir aussi  
 [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [Créer une forme composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)   
 [Créer une forme à l'aide d'un PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)