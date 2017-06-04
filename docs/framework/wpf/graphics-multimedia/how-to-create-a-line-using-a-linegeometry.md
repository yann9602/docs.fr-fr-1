---
title: "Comment&#160;: cr&#233;er une ligne &#224; l&#39;aide d&#39;un LineGeometry | Microsoft Docs"
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
  - "classes, LineGeometry"
  - "graphiques (WPF), lignes"
  - "LineGeometry (classe)"
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: cr&#233;er une ligne &#224; l&#39;aide d&#39;un LineGeometry
Cet exemple montre comment utiliser la classe <xref:System.Windows.Media.LineGeometry> pour décrire une ligne.  Une <xref:System.Windows.Media.LineGeometry> est définie par son point de départ et son point final.  
  
## Exemple  
 L'exemple suivant montre comment créer et rendre un <xref:System.Windows.Media.LineGeometry>.  Un élément <xref:System.Windows.Shapes.Path> est utilisé pour restituer la ligne.  Comme une ligne n'a pas de surface, le <xref:System.Windows.Shapes.Path> de l'objet <xref:System.Windows.Shapes.Shape.Fill%2A> n'est pas spécifié ; les propriétés <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> sont utilisées à la place.  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.png "graphicsmm\_line")  
LineGeometry tracée de \(10,20\) à \(100,130\)  
  
 D'autres classes de géométrie simple incluent <xref:System.Windows.Media.LineGeometry> et <xref:System.Windows.Media.EllipseGeometry>.  Ces géométries, ainsi que d'autres plus complexes, peuvent également être créées à l'aide d'un <xref:System.Windows.Media.PathGeometry> ou d'un <xref:System.Windows.Media.StreamGeometry>.  Pour plus d'informations, consultez [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
## Voir aussi  
 [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [Créer une forme composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)   
 [Créer une forme à l'aide d'un PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)