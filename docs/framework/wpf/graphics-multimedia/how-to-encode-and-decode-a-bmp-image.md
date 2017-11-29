---
title: "Comment : encoder et décoder une image BMP"
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
- encoding BMP images [WPF]
- BMP encoding [WPF]
- decoding BMP images [WPF]
- encoding image formats [WPF]
- BMP decoding [WPF]
- decoding image formats [WPF]
ms.assetid: feb5ef27-28ac-40ab-bfc2-e0456990d32c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c895a8a7c46020fa5277a3e592c7d3e18f02ab6
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a><span data-ttu-id="ab72b-102">Comment : encoder et décoder une image BMP</span><span class="sxs-lookup"><span data-stu-id="ab72b-102">How to: Encode and Decode a BMP Image</span></span>
<span data-ttu-id="ab72b-103">Les exemples suivants montrent comment décoder et encoder une [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] de l’image à l’aide spécifique au <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> et <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> objets.</span><span class="sxs-lookup"><span data-stu-id="ab72b-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] image using the specific <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> and <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab72b-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab72b-104">Example</span></span>  
 <span data-ttu-id="ab72b-105">Cet exemple montre comment décoder une [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] à l’aide de l’image un <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> d’un <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="ab72b-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] image using a <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ab72b-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab72b-106">Example</span></span>  
 <span data-ttu-id="ab72b-107">Cet exemple montre comment encoder un <xref:System.Windows.Media.Imaging.BitmapSource> dans un [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] à l’aide de l’image un <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="ab72b-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] image using a <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ab72b-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab72b-108">See Also</span></span>  
 [<span data-ttu-id="ab72b-109">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="ab72b-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
