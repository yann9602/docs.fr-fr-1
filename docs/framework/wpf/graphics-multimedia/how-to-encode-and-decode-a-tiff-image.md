---
title: "Comment&#160;: encoder et d&#233;coder une image&#160;TIFF | Microsoft Docs"
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
  - "décoder des images TIFF"
  - "formats d'encodage d'images"
  - "encoder des images TIFF"
  - "décodage TIFF"
  - "encodage TIFF"
ms.assetid: 1dfe3209-fc73-40e6-ad1c-71c1c58b3364
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: encoder et d&#233;coder une image&#160;TIFF
Les exemples suivants expliquent comment décoder et encoder une image [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] à l'aide des objets <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> et <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> spécifiques.  
  
## Exemple  
 Cet exemple montre comment décoder une image [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] à l'aide d'un <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> depuis un <xref:System.Uri>.  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## Exemple  
 Cet exemple montre comment encoder un <xref:System.Windows.Media.Imaging.BitmapSource> dans une image [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] à l'aide d'un <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## Voir aussi  
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)