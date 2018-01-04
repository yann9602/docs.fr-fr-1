---
title: "Comment : créer un GeometryDrawing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31417a3eeee2c1e61674c43558c2799705797c35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-geometrydrawing"></a>Comment : créer un GeometryDrawing
Cet exemple montre comment créer et afficher un <xref:System.Windows.Media.GeometryDrawing>. A <xref:System.Windows.Media.GeometryDrawing> vous permet de créer la forme avec un remplissage et un contour en associant un <xref:System.Windows.Media.Pen> et un <xref:System.Windows.Media.Brush> avec un <xref:System.Windows.Media.Geometry>. Le <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> décrit la structure de la forme, le <xref:System.Windows.Media.GeometryDrawing.Brush%2A> décrit le remplissage de la forme et le <xref:System.Windows.Media.GeometryDrawing.Pen%2A> décrit le contour de la forme.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un <xref:System.Windows.Media.GeometryDrawing> pour rendre une forme. La forme est décrite par un <xref:System.Windows.Media.GeometryGroup> et deux <xref:System.Windows.Media.EllipseGeometry> objets. Est peint l’intérieur de la forme avec un <xref:System.Windows.Media.LinearGradientBrush> et son contour est dessiné avec un <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>. Le <xref:System.Windows.Media.GeometryDrawing> est affichée en utilisant un <xref:System.Windows.Media.ImageDrawing> et un <xref:System.Windows.Controls.Image> élément.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 L’illustration suivante montre le qui en résulte <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing de deux ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 Pour créer des dessins plus complexes, vous pouvez combiner plusieurs objets de dessin dans un composite unique à l’aide de dessin un <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.DrawingGroup>  
 [Vue d’ensemble des objets de dessin](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Créer un dessin composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
