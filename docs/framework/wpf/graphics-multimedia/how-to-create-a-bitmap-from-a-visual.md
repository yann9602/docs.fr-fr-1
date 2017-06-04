---
title: "Comment&#160;: cr&#233;er une image bitmap &#224; partir d&#39;un Visual | Microsoft Docs"
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
  - "bitmaps, rendu à partir d'objets visuels"
  - "objets visuels, rendu dans des bitmaps"
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: cr&#233;er une image bitmap &#224; partir d&#39;un Visual
Cet exemple indique comment créer une image bitmap à partir d'un <xref:System.Windows.Media.Visual>.  Un <xref:System.Windows.Media.DrawingVisual> est rendu avec <xref:System.Windows.Media.FormattedText>.  Le <xref:System.Windows.Media.Visual> est ensuite rendu dans le <xref:System.Windows.Media.Imaging.RenderTargetBitmap> pour créer une image bitmap du texte donné.  
  
## Exemple  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## Voir aussi  
 <xref:System.Windows.Media.DrawingContext>   
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Utilisation d'objets DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)