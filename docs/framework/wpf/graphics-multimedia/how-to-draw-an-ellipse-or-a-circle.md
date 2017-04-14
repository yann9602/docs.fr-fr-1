---
title: "Comment&#160;: dessiner une ellipse ou un cercle | Microsoft Docs"
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
  - "cercles, dessiner"
  - "dessiner des cercles"
  - "dessiner des ellipses"
  - "ellipses, dessiner"
  - "graphiques, dessiner des cercles"
  - "graphiques, dessiner des ellipses"
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: dessiner une ellipse ou un cercle
Cet exemple indique comment dessiner des ellipses et des cercles à l'aide de l'élément <xref:System.Windows.Shapes.Ellipse>.  Pour dessiner une ellipse, créez un élément <xref:System.Windows.Shapes.Ellipse> et spécifiez sa <xref:System.Windows.FrameworkElement.Width%2A> et sa <xref:System.Windows.FrameworkElement.Height%2A>.  Utilisez sa propriété <xref:System.Windows.Shapes.Shape.Fill%2A> pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre l'intérieur de l'ellipse.  Utilisez sa propriété <xref:System.Windows.Shapes.Shape.Stroke%2A> pour spécifier le <xref:System.Windows.Media.Brush> utilisé pour peindre le contour de l'ellipse.  La propriété <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> spécifie l'épaisseur du contour de l'ellipse.  
  
 Pour dessiner un cercle, assurez\-vous que la <xref:System.Windows.FrameworkElement.Width%2A> et la <xref:System.Windows.FrameworkElement.Height%2A> de l'élément <xref:System.Windows.Shapes.Ellipse> sont égales.  
  
 L'exemple suivant dessine quatre éléments <xref:System.Windows.Shapes.Ellipse> dans un <xref:System.Windows.Controls.Canvas>.  
  
## Exemple  
 [!code-xml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les ellipses, vous pouvez utiliser des éléments ellipses \(et toutes les autres formes\) avec n'importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Éléments de forme, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## Voir aussi  
 <xref:System.Windows.Shapes.Ellipse>   
 <xref:System.Windows.Shapes.Shape>   
 [Éléments de forme, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160037)