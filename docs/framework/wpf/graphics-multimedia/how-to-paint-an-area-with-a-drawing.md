---
title: "Comment&#160;: peindre une zone avec un dessin | Microsoft Docs"
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
  - "pinceaux, peindre avec des dessins"
  - "dessins, peindre avec"
  - "peindre, avec des dessins"
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: peindre une zone avec un dessin
Cet exemple montre comment peindre une zone avec un dessin.  Pour peindre une zone avec un dessin, utilisez un <xref:System.Windows.Media.DrawingBrush> et un ou plusieurs objets <xref:System.Windows.Media.Drawing>.  L'exemple suivant utilise un <xref:System.Windows.Media.DrawingBrush> pour peindre un objet avec un dessin de deux ellipses.  
  
## Exemple  
 [!code-xml[drawingbrush_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 Le résultat de cet exemple est illustrée ci\-dessous.  
  
 ![Sortie d'un DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm\_drawingbrush\_simple")  
  
 \(Le centre de la forme est blanc pour les raisons décrites dans [Contrôler le remplissage d'une forme composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md).\)  
  
 En définissant les propriétés <xref:System.Windows.Media.TileBrush.Viewport%2A> et <xref:System.Windows.Media.TileBrush.TileMode%2A> d'un objet <xref:System.Windows.Media.DrawingBrush>, vous pouvez créer un motif répété.  L'exemple suivant peint un objet avec un motif créé à partir d'un dessin de deux ellipses.  
  
 [!code-xml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 L'illustration suivante montre le résultat <xref:System.Windows.Media.DrawingBrush> en mosaïque.  
  
 ![Sortie en mosaïque d'un DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm\_drawingbrush\_tiled")  
  
 Pour plus d'informations sur les pinceaux de dessin, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  Pour plus d'informations sur les objets <xref:System.Windows.Media.Drawing>, consultez [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).