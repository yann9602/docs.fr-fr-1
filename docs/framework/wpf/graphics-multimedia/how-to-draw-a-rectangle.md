---
title: "Comment : dessiner un rectangle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c163897af27c9b34c8cd87a3b197047f86d21ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-rectangle"></a>Comment : dessiner un rectangle
Cet exemple montre comment dessiner un rectangle à l’aide de la <xref:System.Windows.Shapes.Rectangle> élément.  
  
 Pour dessiner un rectangle, créez un <xref:System.Windows.Shapes.Rectangle> élément et spécifiez son <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>. Pour peindre l’intérieur du rectangle, définissez son <xref:System.Windows.Shapes.Shape.Fill%2A>. Pour donner le rectangle à un plan, utilisez son <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriétés.  
  
 Le rectangle de donner des angles arrondis, spécifiez le paramètre facultatif <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriétés. Le <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriétés définies les rayons des axes x et y de l’ellipse utilisée pour arrondir les angles du rectangle.  
  
 Dans l’exemple suivant, deux <xref:System.Windows.Shapes.Rectangle> éléments sont dessinées dans une <xref:System.Windows.Controls.Canvas>. Le premier rectangle est un <xref:System.Windows.Media.Brushes.Blue%2A> intérieurs. Le deuxième rectangle a un <xref:System.Windows.Media.Brushes.Blue%2A> intérieurs, une <xref:System.Windows.Media.Brushes.Black%2A> plan et des angles arrondis.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les rectangles, vous pouvez utiliser des éléments de rectangle (et tous les autres éléments de forme) avec n’importe quelle <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel. En fait, les rectangles sont particulièrement utiles pour fournir des arrière-plans pour certaines parties de <xref:System.Windows.Controls.Grid> panneaux. Pour obtenir un exemple, consultez la [vue d’ensemble de la Table](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 Cet exemple fait partie d’un exemple plus complet ; Pour obtenir un exemple complet, consultez [éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Shapes.Rectangle>  
 [Éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [Vue d’ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Vue d’ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md)
