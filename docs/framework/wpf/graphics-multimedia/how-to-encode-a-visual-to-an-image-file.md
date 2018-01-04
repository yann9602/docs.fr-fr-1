---
title: "Comment : encoder un Visual dans un fichier image"
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
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88a5d93c9c4726d1f6493df28d0a2a559394ef74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="15705-102">Comment : encoder un Visual dans un fichier image</span><span class="sxs-lookup"><span data-stu-id="15705-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="15705-103">Cet exemple montre comment encoder un <xref:System.Windows.Media.Visual> objet dans un fichier image à l’aide un <xref:System.Windows.Media.Imaging.RenderTargetBitmap> et un <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="15705-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15705-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="15705-104">Example</span></span>  
 <span data-ttu-id="15705-105">Le <xref:System.Windows.Media.DrawingVisual> est créé en utilisant un <xref:System.Windows.Media.Imaging.BitmapImage> et <xref:System.Windows.Media.FormattedText> est restituée à un <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span><span class="sxs-lookup"><span data-stu-id="15705-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="15705-106">La bitmap rendue est ensuite utilisée pour créer un <xref:System.Windows.Media.Imaging.BitmapFrame> qui est ajouté à la <xref:System.Windows.Media.Imaging.PngBitmapEncoder> pour créer un nouveau [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] fichier.</span><span class="sxs-lookup"><span data-stu-id="15705-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="15705-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> a été utilisé dans cet exemple, mais les dérivé <xref:System.Windows.Media.Imaging.BitmapEncoder> objets pourrait avoir été utilisés pour créer le fichier image.</span><span class="sxs-lookup"><span data-stu-id="15705-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15705-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15705-108">See Also</span></span>  
 <xref:System.Windows.Media.DrawingContext>  
 [<span data-ttu-id="15705-109">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="15705-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="15705-110">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="15705-110">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="15705-111">Utilisation d’objets DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="15705-111">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
