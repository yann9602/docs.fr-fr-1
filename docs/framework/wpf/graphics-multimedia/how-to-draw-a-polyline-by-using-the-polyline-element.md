---
title: "Comment&#160;: dessiner une polyligne &#224; l&#39;aide de l&#39;&#233;l&#233;ment Polyline | Microsoft Docs"
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
  - "lignes reliées"
  - "dessiner, polylignes"
  - "graphiques (WPF), polylignes"
  - "lignes, reliées (voir polylignes)"
  - "polylignes, dessiner"
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: dessiner une polyligne &#224; l&#39;aide de l&#39;&#233;l&#233;ment Polyline
Cet exemple indique comment dessiner une polyligne, c'est\-à\-dire une série de lignes reliées entre elles, à l'aide de l'élément <xref:System.Windows.Shapes.Polyline>.  
  
 Pour dessiner une polyligne, créez un élément <xref:System.Windows.Shapes.Polyline> et utilisez sa propriété <xref:System.Windows.Shapes.Polyline.Points%2A> pour spécifier les vertex de la forme.  Pour finir, utilisez les propriétés <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> pour décrire le contour de la polyligne car une ligne sans trait est invisible.  
  
> [!NOTE]
>  Étant donné que l'élément <xref:System.Windows.Shapes.Polyline> n'est pas une forme fermée, la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> n'a aucun effet, même si vous fermez délibérément le contour de la forme.  Pour créer une forme fermée avec un <xref:System.Windows.Shapes.Shape.Fill%2A>, utilisez un élément <xref:System.Windows.Shapes.Polygon>.  
  
 L'exemple suivant dessine deux éléments <xref:System.Windows.Shapes.Polyline> à l'intérieur d'un <xref:System.Windows.Controls.Canvas>.  
  
## Exemple  
 En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe valide pour des points est une liste de paires de coordonnées x et y, séparées par des virgules, délimitée par des espaces.  
  
 [!code-xml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les polylignes, vous pouvez utiliser des éléments polylignes \(et toutes les autres formes\) avec n'importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.  
  
 Cet exemple est extrait d'un exemple plus complet ; pour l'obtenir, consultez [Éléments de forme, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## Voir aussi  
 <xref:System.Windows.Shapes.Polyline>   
 <xref:System.Windows.Shapes.Polygon>   
 <xref:System.Windows.Shapes.Shape>   
 [Éléments de forme, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160037)   
 [Vue d'ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)