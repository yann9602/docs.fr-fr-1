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
ms.openlocfilehash: adcbd5fb82ce9ae89ac59db5aeb7f384f8cc1fc7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="cfa4a-102">Comment : charger une image en tant que miniature</span><span class="sxs-lookup"><span data-stu-id="cfa4a-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="cfa4a-103">Les exemples suivants montrent comment charger un <xref:System.Windows.Controls.Image> sous forme de miniature pour économiser la mémoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="cfa4a-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfa4a-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="cfa4a-104">Example</span></span>  
 <span data-ttu-id="cfa4a-105">L’exemple suivant définit la <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> propriété d’un <xref:System.Windows.Media.Imaging.BitmapImage> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] afin de réduire la mémoire nécessaire pour charger l’image.</span><span class="sxs-lookup"><span data-stu-id="cfa4a-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="cfa4a-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="cfa4a-106">Example</span></span>  
 <span data-ttu-id="cfa4a-107">L’exemple suivant définit la <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> propriété d’un <xref:System.Windows.Media.Imaging.BitmapImage> dans le code afin de réduire la mémoire nécessaire pour charger l’image.</span><span class="sxs-lookup"><span data-stu-id="cfa4a-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="cfa4a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfa4a-108">See Also</span></span>  
 [<span data-ttu-id="cfa4a-109">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="cfa4a-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
