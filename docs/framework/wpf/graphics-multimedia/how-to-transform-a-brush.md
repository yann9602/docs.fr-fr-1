---
title: "Comment : transformer un pinceau"
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
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ee517eb76877bb4e02c021061055b328597c517
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="630ee-102">Comment : transformer un pinceau</span><span class="sxs-lookup"><span data-stu-id="630ee-102">How to: Transform a Brush</span></span>
<span data-ttu-id="630ee-103">Cet exemple montre comment transformer <xref:System.Windows.Media.Brush> objets à l’aide de leurs deux propriétés de transformation : <xref:System.Windows.Media.Brush.RelativeTransform%2A> et <xref:System.Windows.Media.Brush.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="630ee-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="630ee-104">Les exemples suivants utilisent une <xref:System.Windows.Media.RotateTransform> pour faire pivoter le contenu d’un <xref:System.Windows.Media.ImageBrush> de 45 degrés.</span><span class="sxs-lookup"><span data-stu-id="630ee-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="630ee-105">L’illustration suivante montre le <xref:System.Windows.Media.ImageBrush> sans un <xref:System.Windows.Media.RotateTransform>, avec le <xref:System.Windows.Media.RotateTransform> appliquée à la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété et avec le <xref:System.Windows.Media.RotateTransform> appliquée à la <xref:System.Windows.Media.Brush.Transform%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="630ee-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="630ee-106">![Paramètres de Brush RelativeTransform et Transform](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="630ee-106">![Brush RelativeTransform and Transform settings](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="630ee-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="630ee-107">Example</span></span>  
 <span data-ttu-id="630ee-108">Le premier exemple applique un <xref:System.Windows.Media.RotateTransform> à la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété d’un <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="630ee-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="630ee-109">Le <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés d’un <xref:System.Windows.Media.RotateTransform> de l’objet sont toutes deux définies sur 0,5, ce qui est la coordonnée relative du point central de ce contenu.</span><span class="sxs-lookup"><span data-stu-id="630ee-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="630ee-110">Par conséquent, le <xref:System.Windows.Media.ImageBrush> contenu fait pivoter autour de son centre.</span><span class="sxs-lookup"><span data-stu-id="630ee-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="630ee-111">Le deuxième exemple s’applique également une <xref:System.Windows.Media.RotateTransform> à un <xref:System.Windows.Media.ImageBrush>; Toutefois, cet exemple utilise le <xref:System.Windows.Media.Brush.Transform%2A> propriété au lieu du <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="630ee-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="630ee-112">Pour faire pivoter le pinceau autour de son centre, l’exemple définit le <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés de la <xref:System.Windows.Media.RotateTransform> objet coordonnées absolues.</span><span class="sxs-lookup"><span data-stu-id="630ee-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="630ee-113">Étant donné que le pinceau peint un rectangle de 175 par 90 pixels, le point central du rectangle est (87,5, 45).</span><span class="sxs-lookup"><span data-stu-id="630ee-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="630ee-114">Pour obtenir une description de la façon dont <xref:System.Windows.Media.Brush.RelativeTransform%2A> et <xref:System.Windows.Media.Brush.Transform%2A> propriétés, consultez la [vue d’ensemble de la Transformation de pinceau](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="630ee-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="630ee-115">Pour l’exemple complet, consultez [Exemples de pinceaux](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="630ee-115">For the complete sample, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="630ee-116">Pour plus d’informations sur les pinceaux, consultez [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="630ee-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630ee-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="630ee-117">See Also</span></span>  
 [<span data-ttu-id="630ee-118">Vue d'ensemble des transformations du pinceau</span><span class="sxs-lookup"><span data-stu-id="630ee-118">Brush Transformation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [<span data-ttu-id="630ee-119">Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="630ee-119">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="630ee-120">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="630ee-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
