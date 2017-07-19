---
title: "Comment&#160;: encoder et d&#233;coder une image&#160;JPEG | Microsoft Docs"
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
  - "formats de décodage d'images"
  - "décoder des images JPEG"
  - "formats d'encodage d'images"
  - "encoder des images JPEG"
  - "décodage JPEG"
  - "encodage JPEG"
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: encoder et d&#233;coder une image&#160;JPEG
Les exemples suivants expliquent comment décoder et encoder une image [!INCLUDE[TLA#tla_jpeg](../../../../includes/tlasharptla-jpeg-md.md)] à l'aide des objets <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> et <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> spécifiques.  
  
## Exemple  
 Cet exemple montre comment décoder une image [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] à l'aide d'un <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> depuis un <xref:System.IO.FileStream>.  
  
 [!code-cpp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
 [!code-csharp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
 [!code-vb[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## Exemple  
 Cet exemple montre comment encoder une <xref:System.Windows.Media.Imaging.BitmapSource> dans une image [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] à l'aide d'un <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.  
  
 [!code-cpp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
 [!code-csharp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
 [!code-vb[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## Sécurité .NET Framework  
  
## Voir aussi  
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)