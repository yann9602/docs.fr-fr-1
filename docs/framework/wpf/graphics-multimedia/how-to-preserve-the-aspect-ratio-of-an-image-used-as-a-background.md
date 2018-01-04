---
title: "Comment : conserver les proportions d'une image utilisée comme arrière-plan"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9716d91a99eb79e38b729424389b2962d1eb6b1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a><span data-ttu-id="3f0b0-102">Comment : conserver les proportions d'une image utilisée comme arrière-plan</span><span class="sxs-lookup"><span data-stu-id="3f0b0-102">How to: Preserve the Aspect Ratio of an Image Used as a Background</span></span>
<span data-ttu-id="3f0b0-103">Cet exemple montre comment utiliser le <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété d’un <xref:System.Windows.Media.ImageBrush> afin de conserver les proportions de l’image.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of an <xref:System.Windows.Media.ImageBrush> in order to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="3f0b0-104">Par défaut, lorsque vous utilisez un <xref:System.Windows.Media.ImageBrush> pour peindre une zone, son contenu s’étire pour remplir complètement la zone de sortie.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-104">By default, when you use an <xref:System.Windows.Media.ImageBrush> to paint an area, its content stretches to completely fill the output area.</span></span> <span data-ttu-id="3f0b0-105">Lorsque la zone de sortie et l’image ont des proportions différentes, l’image est déformée par cet étirement.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-105">When the output area and the image have different aspect ratios, the image is distorted by this stretching.</span></span>  
  
 <span data-ttu-id="3f0b0-106">Pour rendre un <xref:System.Windows.Media.ImageBrush> conserve les proportions de son image, affectez le <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété <xref:System.Windows.Media.Stretch.Uniform> ou <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-106">To make an <xref:System.Windows.Media.ImageBrush> preserve the aspect ratio of its image, set the <xref:System.Windows.Media.TileBrush.Stretch%2A> property to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f0b0-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f0b0-107">Example</span></span>  
 <span data-ttu-id="3f0b0-108">L’exemple suivant utilise deux <xref:System.Windows.Media.ImageBrush> objets pour peindre deux rectangles.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-108">The following example uses two <xref:System.Windows.Media.ImageBrush> objects to paint two rectangles.</span></span> <span data-ttu-id="3f0b0-109">Chaque rectangle est de 300 par 150 pixels et chacun contient une image de 300 par 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-109">Each rectangle is 300 by 150 pixels and each contains a 300 by 300 pixel image.</span></span> <span data-ttu-id="3f0b0-110">Le <xref:System.Windows.Media.TileBrush.Stretch%2A> du premier pinceau est définie sur <xref:System.Windows.Media.Stretch.Uniform>et le <xref:System.Windows.Media.TileBrush.Stretch%2A> du deuxième pinceau est définie sur <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-110">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the first brush is set to <xref:System.Windows.Media.Stretch.Uniform>, and the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the second brush is set to <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 <span data-ttu-id="3f0b0-111">L’illustration suivante montre la sortie du premier pinceau, ce qui a un <xref:System.Windows.Media.TileBrush.Stretch%2A> paramètre <xref:System.Windows.Media.Stretch.Uniform>.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-111">The following illustration shows the output of the first brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.Uniform>.</span></span>  
  
 <span data-ttu-id="3f0b0-112">![ImageBrush avec étirement Uniform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span><span class="sxs-lookup"><span data-stu-id="3f0b0-112">![ImageBrush with Uniform stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span></span>  
  
 <span data-ttu-id="3f0b0-113">L’illustration suivante montre la sortie du deuxième pinceau, ce qui a un <xref:System.Windows.Media.TileBrush.Stretch%2A> paramètre <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-113">The next illustration shows the output of the second brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 <span data-ttu-id="3f0b0-114">![ImageBrush avec étirement UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span><span class="sxs-lookup"><span data-stu-id="3f0b0-114">![ImageBrush with UniformToFill stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span></span>  
  
 <span data-ttu-id="3f0b0-115">Notez que la <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété se comporte comme pour les autres <xref:System.Windows.Media.TileBrush> des objets, autrement dit, pour <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-115">Note that the <xref:System.Windows.Media.TileBrush.Stretch%2A> property behaves identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="3f0b0-116">Pour plus d’informations sur <xref:System.Windows.Media.ImageBrush> et l’autre <xref:System.Windows.Media.TileBrush> , consultez [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="3f0b0-116">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="3f0b0-117">Notez également que, bien que le <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété s’affiche, indiquez comment la <xref:System.Windows.Media.TileBrush> contenu s’étire pour s’ajuster à sa zone de sortie, elle spécifie en fait la <xref:System.Windows.Media.TileBrush> contenu s’étire pour remplir sa mosaïque de base.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-117">Note also that, although the <xref:System.Windows.Media.TileBrush.Stretch%2A> property appears to specify how the <xref:System.Windows.Media.TileBrush> content stretches to fit its output area, it actually specifies how the <xref:System.Windows.Media.TileBrush> content stretches to fill its base tile.</span></span> <span data-ttu-id="3f0b0-118">Pour plus d'informations, consultez <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-118">For more information, see <xref:System.Windows.Media.TileBrush>.</span></span>  
  
 <span data-ttu-id="3f0b0-119">Cet exemple de code fait partie d’un exemple plus complet fourni pour la <xref:System.Windows.Media.ImageBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-119">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="3f0b0-120">Pour obtenir un exemple complet, consultez [ImageBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="3f0b0-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f0b0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f0b0-121">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="3f0b0-122">Peinture avec des images, des dessins et des objets visuels</span><span class="sxs-lookup"><span data-stu-id="3f0b0-122">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
