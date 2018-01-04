---
title: "Comment : animer un objet sur un tracé (animation de matrice avec accumulation d'offsets)"
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
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5259e930060a8ac6118d232f08d02193a6a1b300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="8148e-102">Comment : animer un objet sur un tracé (animation de matrice avec accumulation d'offsets)</span><span class="sxs-lookup"><span data-stu-id="8148e-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="8148e-103">Cet exemple montre comment utiliser la <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> classe pour animer un objet le long d’un chemin d’accès et de faire en sorte que cette animation accumule ses décalage des valeurs qu’elle se répète.</span><span class="sxs-lookup"><span data-stu-id="8148e-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8148e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8148e-104">Example</span></span>  
 <span data-ttu-id="8148e-105">L’exemple suivant utilise le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objet à animer la <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriété d’un <xref:System.Windows.Media.MatrixTransform> appliqué à un bouton.</span><span class="sxs-lookup"><span data-stu-id="8148e-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="8148e-106">Le bouton se déplace alors le long d’un tracé courbe.</span><span class="sxs-lookup"><span data-stu-id="8148e-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="8148e-107">En outre, l’exemple définit le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> propriété `true`, ce qui entraîne le décalage de la matrice animée s’accumulent lors de l’animation se répète.</span><span class="sxs-lookup"><span data-stu-id="8148e-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="8148e-108">Étant donné que les valeurs d’offset s’accumulent, le bouton s’éloigne sur l’écran lorsque l’animation se répète, sans revenir à sa position de départ.</span><span class="sxs-lookup"><span data-stu-id="8148e-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="8148e-109">Notez que, bien que le <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> propriété entraîne des valeurs offset s’accumuler au fil des répétitions, elle n’entraîne pas les valeurs de rotation à cumuler.</span><span class="sxs-lookup"><span data-stu-id="8148e-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="8148e-110">Pour rendre les valeurs de rotation s’accumulent, valeur de l’animation <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> et <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> propriétés `true`.</span><span class="sxs-lookup"><span data-stu-id="8148e-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="8148e-111">Pour obtenir un exemple complet, consultez [exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="8148e-111">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="8148e-112">Pour obtenir un exemple montrant comment animer un <xref:System.Windows.Media.Matrix> valeur sur un chemin sans accumulation d’offsets, consultez [animer un objet le long d’un chemin d’accès (Animation de matrice)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="8148e-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8148e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8148e-113">See Also</span></span>  
 [<span data-ttu-id="8148e-114">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="8148e-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="8148e-115">Guides pratiques relatifs aux animations de tracés</span><span class="sxs-lookup"><span data-stu-id="8148e-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
