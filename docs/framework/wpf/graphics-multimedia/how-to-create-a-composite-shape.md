---
title: "Comment&#160;: cr&#233;er une forme composite | Microsoft Docs"
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
  - "formes composites"
  - "graphiques, formes composites"
  - "formes, composites"
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er une forme composite
Cet exemple montre comment créer des formes composites à l'aide d'objets <xref:System.Windows.Media.Geometry> et les afficher à l'aide d'un élément <xref:System.Windows.Shapes.Path>.  Dans l'exemple suivant, une <xref:System.Windows.Media.LineGeometry>, une <xref:System.Windows.Media.EllipseGeometry> et un <xref:System.Windows.Media.RectangleGeometry> sont utilisés avec un <xref:System.Windows.Media.GeometryGroup> pour créer une forme composite.  Les géométries sont ensuite dessinées à l'aide d'un élément <xref:System.Windows.Shapes.Path>.  
  
## Exemple  
 [!code-xml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 L'illustration suivante montre la forme créée dans l'exemple précédent.  
  
 ![Géométrie composée créée à l'aide de GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.png "wcpsdk\_graphicsmm\_compositegeometryexample1")  
Géométrie composite  
  
 Il est possible de créer des formes plus complexes, telles que des polygones et des formes intégrant des segments courbés, à l'aide d'un <xref:System.Windows.Media.PathGeometry>.  Pour obtenir un exemple montrant comment créer une forme à l'aide d'un <xref:System.Windows.Media.PathGeometry>, consultez [Créer une forme à l'aide d'un PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  Bien que cet exemple restitue une forme à l'écran à l'aide d'un élément <xref:System.Windows.Shapes.Path>, des objets <xref:System.Windows.Media.Geometry> peuvent également être utilisés pour décrire le contenu d'un <xref:System.Windows.Media.GeometryDrawing> ou d'un <xref:System.Windows.Media.DrawingContext>.  Ils peuvent également être utilisés pour des découpages et des tests de positionnement.  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Géométries, exemple](http://go.microsoft.com/fwlink/?LinkID=159989).