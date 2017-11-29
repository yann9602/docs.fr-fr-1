---
title: "Comment : encoder et décoder une image PNG"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- PNG encoding [WPF]
- decoding PNG images [WPF]
- PNG decoding [WPF]
- encoding image formats [WPF]
- decoding image formats [WPF]
- encoding PNG images [WPF]
ms.assetid: 3d31d186-af73-47f0-b5a7-c26ae46409a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3687beb2f661b04c79d382bb7bbff6e0f7999924
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-encode-and-decode-a-png-image"></a>Comment : encoder et décoder une image PNG
Les exemples suivants montrent comment décoder et encoder une [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] de l’image à l’aide spécifique au <xref:System.Windows.Media.Imaging.PngBitmapDecoder> et <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objets.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment décoder une [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] à l’aide de l’image un <xref:System.Windows.Media.Imaging.PngBitmapDecoder> d’un <xref:System.IO.FileStream>.  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment encoder un <xref:System.Windows.Media.Imaging.BitmapSource> dans un [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] à l’aide de l’image un <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la création d’images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
