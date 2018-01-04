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
ms.workload: dotnet
ms.openlocfilehash: 0fa304515e508fab246a6946c5a8026369cda250
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-and-decode-a-png-image"></a><span data-ttu-id="b9f45-102">Comment : encoder et décoder une image PNG</span><span class="sxs-lookup"><span data-stu-id="b9f45-102">How to: Encode and Decode a PNG Image</span></span>
<span data-ttu-id="b9f45-103">Les exemples suivants montrent comment décoder et encoder une [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] de l’image à l’aide spécifique au <xref:System.Windows.Media.Imaging.PngBitmapDecoder> et <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objets.</span><span class="sxs-lookup"><span data-stu-id="b9f45-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] image using the specific <xref:System.Windows.Media.Imaging.PngBitmapDecoder> and <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9f45-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9f45-104">Example</span></span>  
 <span data-ttu-id="b9f45-105">Cet exemple montre comment décoder une [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] à l’aide de l’image un <xref:System.Windows.Media.Imaging.PngBitmapDecoder> d’un <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="b9f45-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="b9f45-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9f45-106">Example</span></span>  
 <span data-ttu-id="b9f45-107">Cet exemple montre comment encoder un <xref:System.Windows.Media.Imaging.BitmapSource> dans un [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] à l’aide de l’image un <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="b9f45-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b9f45-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9f45-108">See Also</span></span>  
 [<span data-ttu-id="b9f45-109">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="b9f45-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
