---
title: "Comment&#160;: encoder un Visual dans un fichier image | Microsoft Docs"
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
  - "formats d'encodage d'images"
  - "fichiers image, encoder à partir d'objets visuels"
  - "objets visuels, encoder dans un fichier image"
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: encoder un Visual dans un fichier image
Cet exemple montre comment encoder un objet <xref:System.Windows.Media.Visual> dans un fichier image à l'aide d'un <xref:System.Windows.Media.Imaging.RenderTargetBitmap> et un <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
## Exemple  
 Le <xref:System.Windows.Media.DrawingVisual> est créé à l'aide d'un <xref:System.Windows.Media.Imaging.BitmapImage> et <xref:System.Windows.Media.FormattedText> restitués à un <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.  La bitmap rendue est ensuite utilisée pour créer un <xref:System.Windows.Media.Imaging.BitmapFrame> ajouté au <xref:System.Windows.Media.Imaging.PngBitmapEncoder> pour créer un nouveau fichier [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)].  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 Un <xref:System.Windows.Media.Imaging.PngBitmapEncoder> a été utilisé dans cet exemple mais chacun des objets <xref:System.Windows.Media.Imaging.BitmapEncoder> dérivés aurait pu être utilisé pour créer le fichier image.  
  
## Voir aussi  
 <xref:System.Windows.Media.DrawingContext>   
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Utilisation d'objets DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)