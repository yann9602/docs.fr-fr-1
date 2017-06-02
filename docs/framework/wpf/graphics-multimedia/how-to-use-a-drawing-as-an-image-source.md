---
title: "Comment&#160;: utiliser un dessin comme source d&#39;image | Microsoft Docs"
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
  - "dessins, en tant que sources d'images"
  - "graphiques, dessins, en tant que sources d'images"
  - "sources d'images, dessins"
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: utiliser un dessin comme source d&#39;image
Cet exemple indique comment utiliser un <xref:System.Windows.Media.Drawing> comme <xref:System.Windows.Controls.Image.Source%2A> pour un contrôle <xref:System.Windows.Controls.Image>.  Pour afficher un <xref:System.Windows.Media.Drawing> avec un contrôle <xref:System.Windows.Controls.Image>, utilisez un <xref:System.Windows.Media.DrawingImage> comme contrôle du <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Image.Source%2A> et affectez à la propriété <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=fullName> de l'objet <xref:System.Windows.Media.DrawingImage> le dessin que vous souhaitez afficher.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.DrawingImage> et un contrôle <xref:System.Windows.Controls.Image> pour afficher un <xref:System.Windows.Media.GeometryDrawing>.  Cet exemple produit la sortie suivante :  
  
 ![GeometryDrawing de deux ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## Voir aussi  
 <xref:System.Windows.Freezable.Freeze%2A>   
 [Dessiner une image à l'aide d'ImageDrawing](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [PresentationOptions:Freeze, attribut](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)