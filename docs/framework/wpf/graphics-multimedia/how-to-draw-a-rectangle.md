---
title: "Comment&#160;: dessiner un rectangle | Microsoft Docs"
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
  - "dessiner, rectangles"
  - "graphiques (WPF), rectangles"
  - "rectangles, dessiner"
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: dessiner un rectangle
Cet exemple indique comment dessiner un rectangle à l'aide de l'élément <xref:System.Windows.Shapes.Rectangle>.  
  
 Pour dessiner un rectangle, créez un élément <xref:System.Windows.Shapes.Rectangle> et spécifiez sa <xref:System.Windows.FrameworkElement.Width%2A> et sa <xref:System.Windows.FrameworkElement.Height%2A>.  Pour peindre l'intérieur du rectangle, définissez son <xref:System.Windows.Shapes.Shape.Fill%2A>.  Pour donner un contour au rectangle, utilisez ses propriétés <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.  
  
 Pour donner des angles arrondis au rectangle, spécifiez les propriétés facultatives <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>.  Les propriétés <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> définissent le rayon d'axe x et celui d'axe y de l'ellipse utilisée pour arrondir les angles du rectangle.  
  
 Dans l'exemple suivant, deux éléments <xref:System.Windows.Shapes.Rectangle> sont dessinés dans un <xref:System.Windows.Controls.Canvas>.  Le premier rectangle est <xref:System.Windows.Media.Brushes.Blue%2A> à l'intérieur.  Le deuxième rectangle est <xref:System.Windows.Media.Brushes.Blue%2A> à l'intérieur, son contour est <xref:System.Windows.Media.Brushes.Black%2A> et ses angles sont arrondis.  
  
## Exemple  
 [!code-xml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les rectangles, vous pouvez utiliser des éléments Rectangle \(ou toutes autres formes\) avec n'importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.  En fait, les rectangles sont particulièrement utiles pour fournir des arrière\-plans à certaines parties des panneaux <xref:System.Windows.Controls.Grid>.  Pour obtenir un exemple, consultez [Vue d'ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Éléments de forme, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## Voir aussi  
 <xref:System.Windows.Shapes.Rectangle>   
 [Éléments de forme, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160037)   
 [Vue d'ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [Vue d'ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md)