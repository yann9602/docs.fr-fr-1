---
title: "Comment : charger une image en tant que miniature"
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
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e91e032162e6e652daf18268d05c2a7db291bfc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="29f91-102">Comment : charger une image en tant que miniature</span><span class="sxs-lookup"><span data-stu-id="29f91-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="29f91-103">Les exemples suivants montrent comment charger un <xref:System.Windows.Controls.Image> sous forme de miniature pour économiser la mémoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="29f91-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29f91-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="29f91-104">Example</span></span>  
 <span data-ttu-id="29f91-105">L’exemple suivant définit la <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> propriété d’un <xref:System.Windows.Media.Imaging.BitmapImage> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] afin de réduire la mémoire nécessaire pour charger l’image.</span><span class="sxs-lookup"><span data-stu-id="29f91-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="29f91-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="29f91-106">Example</span></span>  
 <span data-ttu-id="29f91-107">L’exemple suivant définit la <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> propriété d’un <xref:System.Windows.Media.Imaging.BitmapImage> dans le code afin de réduire la mémoire nécessaire pour charger l’image.</span><span class="sxs-lookup"><span data-stu-id="29f91-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="29f91-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f91-108">See Also</span></span>  
 [<span data-ttu-id="29f91-109">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="29f91-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
