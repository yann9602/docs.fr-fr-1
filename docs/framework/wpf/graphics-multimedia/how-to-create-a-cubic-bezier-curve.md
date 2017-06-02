---
title: "Comment&#160;: cr&#233;er une courbe de B&#233;zier cubique | Microsoft Docs"
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
  - "courbes de Bézier, cubiques"
  - "créer, courbes de Bézier cubiques"
  - "courbes de Bézier cubiques"
  - "courbes, de Bézier cubiques"
  - "graphiques, courbes de Bézier cubiques"
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er une courbe de B&#233;zier cubique
Cet exemple montre comment créer une courbe de Bézier cubique.  Pour créer une courbe de Bézier cubique, utilisez les classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure> et <xref:System.Windows.Media.BezierSegment>.  Pour afficher la géométrie résultante, utilisez un élément <xref:System.Windows.Shapes.Path> ou utilisez\-le avec un <xref:System.Windows.Media.GeometryDrawing> ou un <xref:System.Windows.Media.DrawingContext>.  Dans les exemples suivants, une courbe de Bézier cubique est tracée de \(10, 100\) à \(300, 100\).  La courbe a des points de contrôle \(100, 0\) et \(200, 200\).  
  
## Exemple  
 \[xaml\]  
  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez utiliser la syntaxe de balise abrégée pour décrire un chemin d'accès.  
  
 [!code-xml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 \[xaml\]  
  
 Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également tracer une courbe de Bézier cubique à l'aide de balises d'objet.  L'exemple suivant est équivalent à l'exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.  
  
 [!code-xml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Géométries, exemple](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## Voir aussi  
 [Créer un arc elliptique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)   
 [Créer un LineSegment dans un PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)   
 [Create a Cubic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)   
 [Créer une courbe de Bézier quadratique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)