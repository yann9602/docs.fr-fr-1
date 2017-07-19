---
title: "Comment&#160;: cr&#233;er une forme &#224; l&#39;aide d&#39;un PathGeometry | Microsoft Docs"
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
  - "classes, PathGeometry"
  - "graphiques (WPF), formes"
  - "PathGeometry (classe)"
  - "formes, créer avec la classe PathGeometry"
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: cr&#233;er une forme &#224; l&#39;aide d&#39;un PathGeometry
Cet exemple montre comment créer une forme à l'aide de la classe <xref:System.Windows.Media.PathGeometry>.  Les objets <xref:System.Windows.Media.PathGeometry> sont composés d'un ou plusieurs objets <xref:System.Windows.Media.PathFigure>, chaque <xref:System.Windows.Media.PathFigure> représentant une « figure » ou forme différente.  Chaque <xref:System.Windows.Media.PathFigure> est lui\-même composé d'un ou plusieurs objets <xref:System.Windows.Media.PathSegment>, chacun représentant une partie connectée de l'illustration ou forme.  Les types de segments incluent <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment> et <xref:System.Windows.Media.BezierSegment>.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.PathGeometry> pour créer un triangle.  Le <xref:System.Windows.Media.PathGeometry> est affiché à l'aide d'un élément <xref:System.Windows.Shapes.Path>.  
  
 [!code-xml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 L'illustration suivante montre la forme créée dans l'exemple précédent.  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.png "wcpsdk\_graphicsmm\_pathgeometry\_triangle")  
Un triangle créé avec un PathGeometry  
  
 L'exemple précédent a montré comment créer une forme relativement simple, un triangle.  Un <xref:System.Windows.Media.PathGeometry> peut également être utilisé pour créer des formes plus complexes, y compris les arcs et courbes.  Pour obtenir des exemples, consultez [Créer un arc elliptique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [Créer une courbe de Bézier cubique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md) et [Créer une courbe de Bézier quadratique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Géométries, exemple](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## Voir aussi  
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.GeometryDrawing>   
 [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [Géométries, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159989)