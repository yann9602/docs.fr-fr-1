---
title: "Comment : peindre une zone avec une vidéo"
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
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 362231bbd1f4e95c260370a99233b7e8c2617ca1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="27414-102">Comment : peindre une zone avec une vidéo</span><span class="sxs-lookup"><span data-stu-id="27414-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="27414-103">Cet exemple montre comment peindre une zone avec le média.</span><span class="sxs-lookup"><span data-stu-id="27414-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="27414-104">Une façon de peindre une zone avec un support consiste à utiliser un <xref:System.Windows.Controls.MediaElement> avec un <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="27414-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="27414-105">Utilisez le <xref:System.Windows.Controls.MediaElement> pour charger et lire le média, puis utilisez-la pour définir le <xref:System.Windows.Media.VisualBrush.Visual%2A> propriété de la <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="27414-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="27414-106">Vous pouvez ensuite utiliser le <xref:System.Windows.Media.VisualBrush> pour peindre une zone avec le média chargé.</span><span class="sxs-lookup"><span data-stu-id="27414-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27414-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="27414-107">Example</span></span>  
 <span data-ttu-id="27414-108">L’exemple suivant utilise un <xref:System.Windows.Controls.MediaElement> et un <xref:System.Windows.Media.VisualBrush> pour peindre le <xref:System.Windows.Controls.TextBlock.Foreground%2A> d’un <xref:System.Windows.Controls.TextBlock> contrôle vidéo.</span><span class="sxs-lookup"><span data-stu-id="27414-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="27414-109">Cet exemple définit le <xref:System.Windows.Controls.MediaElement.IsMuted%2A> propriété de la <xref:System.Windows.Controls.MediaElement> à `true` pour qu’il ne produise aucun son.</span><span class="sxs-lookup"><span data-stu-id="27414-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="27414-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="27414-110">Example</span></span>  
 <span data-ttu-id="27414-111">Étant donné que <xref:System.Windows.Media.VisualBrush> hérite le <xref:System.Windows.Media.TileBrush> (classe), il fournit plusieurs modes de mosaïque.</span><span class="sxs-lookup"><span data-stu-id="27414-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="27414-112">En définissant le <xref:System.Windows.Media.TileBrush.TileMode%2A> propriété d’un <xref:System.Windows.Media.VisualBrush> à <xref:System.Windows.Media.TileMode.Tile> et en définissant son <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété à une valeur inférieure à la zone qui vous sont en train de peindre, vous pouvez créer un modèle en mosaïque.</span><span class="sxs-lookup"><span data-stu-id="27414-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="27414-113">L’exemple suivant est identique à l’exemple précédent, à ceci près que le <xref:System.Windows.Media.VisualBrush> génère un modèle à partir de la vidéo.</span><span class="sxs-lookup"><span data-stu-id="27414-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="27414-114">Pour plus d’informations sur l’ajout d’un fichier de contenu, tel qu’un fichier multimédia, à votre application, consultez [ressource d’Application WPF, contenu et les fichiers de données](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="27414-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="27414-115">Lorsque vous ajoutez un fichier multimédia, vous devez l’ajouter en tant qu’un fichier de contenu, et non comme un fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="27414-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27414-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27414-116">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="27414-117">Peinture avec des images, des dessins et des objets visuels</span><span class="sxs-lookup"><span data-stu-id="27414-117">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="27414-118">Vue d’ensemble de TileBrush</span><span class="sxs-lookup"><span data-stu-id="27414-118">TileBrush Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [<span data-ttu-id="27414-119">Vue d’ensemble multimédia</span><span class="sxs-lookup"><span data-stu-id="27414-119">Multimedia Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
