---
title: "Comment&#160;: cr&#233;er un GeometryDrawing | Microsoft Docs"
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
  - "classes, GeometryDrawing"
  - "GeometryDrawing (classe)"
  - "graphiques, GeometryDrawing (classe)"
  - "formes pouvant être rendues"
  - "formes, pouvant être rendues"
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er un GeometryDrawing
Cet exemple indique comment créer et afficher un <xref:System.Windows.Media.GeometryDrawing>.  Un <xref:System.Windows.Media.GeometryDrawing> vous permet de créer une forme avec un remplissage et un contour en associant <xref:System.Windows.Media.Pen> et <xref:System.Windows.Media.Brush> à <xref:System.Windows.Media.Geometry>.  <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> décrit la structure de la forme, <xref:System.Windows.Media.GeometryDrawing.Brush%2A> décrit le remplissage et <xref:System.Windows.Media.GeometryDrawing.Pen%2A>, le contour.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation d'un <xref:System.Windows.Media.GeometryDrawing> pour rendre une forme.  La forme est décrite par un <xref:System.Windows.Media.GeometryGroup> et deux objets <xref:System.Windows.Media.EllipseGeometry>.  L'intérieur de la forme est peint avec un <xref:System.Windows.Media.LinearGradientBrush> et son contour est dessiné avec un <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  Le <xref:System.Windows.Media.GeometryDrawing> est affiché à l'aide d'un <xref:System.Windows.Media.ImageDrawing> et d'un élément <xref:System.Windows.Controls.Image>.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 L'illustration suivante montre le <xref:System.Windows.Media.GeometryDrawing> qui en résulte.  
  
 ![GeometryDrawing de deux ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
  
 Pour créer des dessins plus complexes, vous pouvez combiner plusieurs objets de dessin dans un dessin composite unique à l'aide d'un <xref:System.Windows.Media.DrawingGroup>.  
  
## Voir aussi  
 <xref:System.Windows.Media.DrawingGroup>   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [Créer un dessin composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)