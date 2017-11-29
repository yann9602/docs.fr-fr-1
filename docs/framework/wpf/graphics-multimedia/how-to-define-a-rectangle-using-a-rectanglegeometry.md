---
title: "Comment : définir un rectangle à l'aide d'un RectangleGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 678d6f36c02c63825782b9f1c860285450a6a9f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>Comment : définir un rectangle à l'aide d'un RectangleGeometry
Cet exemple explique comment utiliser la <xref:System.Windows.Media.RectangleGeometry> classe pour décrire un rectangle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer et restituer un <xref:System.Windows.Media.RectangleGeometry>.  La position relative et les dimensions du rectangle sont définies par un <xref:System.Windows.Rect> structure. La position relative est `50,50` et la hauteur et la largeur sont toutes deux `25` création d’un carré. L’intérieur du rectangle est peint avec un <xref:System.Windows.Media.Brushes.LemonChiffon%2A> pinceau et son plan est peint avec un <xref:System.Windows.Media.Brushes.Black%2A> une épaisseur de trait `1`.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 Bien que cet exemple utilise un <xref:System.Windows.Shapes.Path> élément à restituer le <xref:System.Windows.Media.RectangleGeometry>, il existe plusieurs autres façons d’utiliser <xref:System.Windows.Media.RectangleGeometry> objets. Par exemple, un <xref:System.Windows.Media.RectangleGeometry> peut être utilisé pour spécifier le <xref:System.Windows.UIElement.Clip%2A> d’un <xref:System.Windows.UIElement> ou le <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> d’un <xref:System.Windows.Media.GeometryDrawing>.  
  
 Autres classes de géométrie simple incluent <xref:System.Windows.Media.LineGeometry> et <xref:System.Windows.Media.EllipseGeometry>. Ces géométries, ainsi que ceux qui sont plus complexes, peut également être créés en utilisant un <xref:System.Windows.Media.PathGeometry> ou <xref:System.Windows.Media.StreamGeometry>.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Créer une forme composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Créer une forme à l’aide d’un PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
