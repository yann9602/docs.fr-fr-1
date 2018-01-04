---
title: "Comment : animer un point à l'aide d'images clés"
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
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c115d31c6ace26f8fd9dd6cff3fdeead89eea33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="780a8-102">Comment : animer un point à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="780a8-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="780a8-103">Cet exemple montre comment utiliser le <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe pour animer une <xref:System.Windows.Point>.</span><span class="sxs-lookup"><span data-stu-id="780a8-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="780a8-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="780a8-104">Example</span></span>  
 <span data-ttu-id="780a8-105">L’exemple suivant déplace une ellipse sur un tracé triangulaire.</span><span class="sxs-lookup"><span data-stu-id="780a8-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="780a8-106">L’exemple utilise le <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe pour animer la <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriété d’un <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="780a8-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="780a8-107">Cette animation utilise trois images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="780a8-107">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="780a8-108">Pendant la première demi-seconde, utilise une instance de la <xref:System.Windows.Media.Animation.LinearPointKeyFrame> classe pour déplacer l’ellipse le long d’un chemin d’accès à un taux stable à partir de sa position de départ.</span><span class="sxs-lookup"><span data-stu-id="780a8-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="780a8-109">Images clés linéaires comme <xref:System.Windows.Media.Animation.LinearPointKeyFrame> créent une interpolation linéaire fluide entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="780a8-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="780a8-110">À la fin de la prochaine demi-seconde, utilise une instance de la <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> classe pour déplacer soudainement l’ellipse le long du chemin d’accès à la position suivante.</span><span class="sxs-lookup"><span data-stu-id="780a8-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="780a8-111">Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> créer soudains entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="780a8-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3.  <span data-ttu-id="780a8-112">Pendant les deux dernières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.SplinePointKeyFrame> classe pour ramener l’ellipse à sa position de départ.</span><span class="sxs-lookup"><span data-stu-id="780a8-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="780a8-113">Les images clés spline comme <xref:System.Windows.Media.Animation.SplinePointKeyFrame> créer une transition entre des valeurs en fonction des valeurs de la <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="780a8-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="780a8-114">Dans cet exemple, l’animation commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.</span><span class="sxs-lookup"><span data-stu-id="780a8-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="780a8-115">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="780a8-115">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="780a8-116">Par souci de cohérence avec d’autres exemples d’animation, les versions de code de cet exemple montre comment utilisent un <xref:System.Windows.Media.Animation.Storyboard> objet pour appliquer le <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="780a8-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="780a8-117">Toutefois, lorsque vous appliquez une animation unique dans le code, il est plus simple d’utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode au lieu d’utiliser un <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="780a8-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="780a8-118">Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="780a8-118">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="780a8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="780a8-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [<span data-ttu-id="780a8-120">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="780a8-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="780a8-121">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="780a8-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
