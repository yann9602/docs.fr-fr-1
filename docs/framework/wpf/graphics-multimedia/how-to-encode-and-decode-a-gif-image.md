---
title: "Comment&#160;: encoder et d&#233;coder une image&#160;GIF | Microsoft Docs"
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
  - "décoder des images GIF"
  - "formats de décodage d'images"
  - "encoder des images GIF"
  - "formats d'encodage d'images"
  - "décodage GIF"
  - "encodage GIF"
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: encoder et d&#233;coder une image&#160;GIF
Les exemples suivants expliquent comment décoder et encoder une image [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] à l'aide des objets <xref:System.Windows.Media.Imaging.GifBitmapDecoder> et <xref:System.Windows.Media.Imaging.GifBitmapEncoder> spécifiques.  
  
## Exemple  
 Cet exemple montre comment décoder une image [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] à l'aide d'un <xref:System.Windows.Media.Imaging.GifBitmapDecoder> depuis un <xref:System.IO.FileStream>.  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## Exemple  
 Cet exemple montre comment encoder une <xref:System.Windows.Media.Imaging.BitmapSource> dans une image [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] à l'aide d'un <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## Voir aussi  
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)