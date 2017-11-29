---
title: "Comment : encoder et décoder une image JPEG"
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
- encoding image formats [WPF]
- decoding JPEG images [WPF]
- encoding JPEG images [WPF]
- decoding image formats [WPF]
- JPEG decoding [WPF]
- JPEG encoding [WPF]
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb432c4609fc873014c39a95e0029584e4d44f93
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="b4464-102">Comment : encoder et décoder une image JPEG</span><span class="sxs-lookup"><span data-stu-id="b4464-102">How to: Encode and Decode a JPEG Image</span></span>
<span data-ttu-id="b4464-103">Les exemples suivants montrent comment décoder et encoder une [!INCLUDE[TLA#tla_jpeg](../../../../includes/tlasharptla-jpeg-md.md)] de l’image à l’aide spécifique au <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> et <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objets.</span><span class="sxs-lookup"><span data-stu-id="b4464-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_jpeg](../../../../includes/tlasharptla-jpeg-md.md)] image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4464-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b4464-104">Example</span></span>  
 <span data-ttu-id="b4464-105">Cet exemple montre comment décoder une [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] à l’aide de l’image un <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> d’un <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="b4464-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
 [!code-csharp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
 [!code-vb[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="b4464-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="b4464-106">Example</span></span>  
 <span data-ttu-id="b4464-107">Cet exemple montre comment encoder un <xref:System.Windows.Media.Imaging.BitmapSource> dans un [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] à l’aide de l’image un <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="b4464-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
 [!code-cpp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
 [!code-csharp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
 [!code-vb[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="b4464-108">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4464-108">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4464-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4464-109">See Also</span></span>  
 [<span data-ttu-id="b4464-110">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="b4464-110">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
