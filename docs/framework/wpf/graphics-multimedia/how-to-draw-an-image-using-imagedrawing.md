---
title: "Comment&#160;: dessiner une image &#224; l&#39;aide d&#39;ImageDrawing | Microsoft Docs"
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
  - "classes, ImageDrawing"
  - "dessiner, images"
  - "graphiques, dessiner des images"
  - "ImageDrawing (classe)"
  - "images, dessiner"
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: dessiner une image &#224; l&#39;aide d&#39;ImageDrawing
Cet exemple indique comment utiliser un <xref:System.Windows.Media.ImageDrawing> pour dessiner une image.  Un <xref:System.Windows.Media.ImageDrawing> vous permet d'afficher une <xref:System.Windows.Media.ImageSource> avec un <xref:System.Windows.Media.DrawingBrush>, un <xref:System.Windows.Media.DrawingImage> ou un <xref:System.Windows.Media.Visual>.  Pour dessiner une image, créez un <xref:System.Windows.Media.ImageDrawing> et définissez ses propriétés <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=fullName> et <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=fullName>.  La propriété <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=fullName> spécifie l'image à dessiner, tandis que la propriété <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=fullName> spécifie la position et la taille de chaque image.  
  
## Exemple  
 L'exemple suivant crée un dessin composite à l'aide de quatre objets <xref:System.Windows.Media.ImageDrawing>.  Cet exemple génère l'image suivante :  
  
 ![Plusieurs objets DrawingImage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.png "graphicsmm\_ImageDrawingExample")  
Quatre objets ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 Pour obtenir un exemple de méthode simple pour afficher une image sans utiliser <xref:System.Windows.Media.ImageDrawing>, consultez [Utiliser l'élément Image](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).  
  
## Voir aussi  
 <xref:System.Windows.Freezable.Freeze%2A>   
 <xref:System.Windows.Controls.Image>   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [PresentationOptions:Freeze, attribut](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)