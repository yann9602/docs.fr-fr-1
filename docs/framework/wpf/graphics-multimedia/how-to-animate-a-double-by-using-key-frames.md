---
title: "Comment : animer un double à l'aide d'images clés"
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
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c4ec6554ee024450e397ee7757649be7537eaae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="5e067-102">Comment : animer un double à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="5e067-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="5e067-103">Cet exemple montre comment animer la valeur d’une propriété qui prend un <xref:System.Double> à l’aide d’images clés.</span><span class="sxs-lookup"><span data-stu-id="5e067-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e067-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="5e067-104">Example</span></span>  
 <span data-ttu-id="5e067-105">L’exemple suivant déplace un rectangle sur l’écran.</span><span class="sxs-lookup"><span data-stu-id="5e067-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="5e067-106">L’exemple utilise le <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classe pour animer la <xref:System.Windows.Media.TranslateTransform.X%2A> propriété d’un <xref:System.Windows.Media.TranslateTransform> appliqué à un <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="5e067-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="5e067-107">Cette animation, répétée indéfiniment, utilise trois images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="5e067-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="5e067-108">Pendant les trois premières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> classe pour déplacer le rectangle le long d’un chemin d’accès à un taux stable à partir de sa position de départ à la position 500.</span><span class="sxs-lookup"><span data-stu-id="5e067-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="5e067-109">Images clés linéaires comme <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> créer une transition linéaire fluide entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="5e067-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="5e067-110">À la fin de la quatrième seconde, utilise une instance de la <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> classe pour déplacer soudainement le rectangle à la position suivante.</span><span class="sxs-lookup"><span data-stu-id="5e067-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="5e067-111">Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> créer soudains entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="5e067-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="5e067-112">Dans cet exemple, le rectangle se trouve à la position de départ et passe subitement à la position 500.</span><span class="sxs-lookup"><span data-stu-id="5e067-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3.  <span data-ttu-id="5e067-113">Dans les deux dernières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> classe pour ramener le rectangle à sa position de départ.</span><span class="sxs-lookup"><span data-stu-id="5e067-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="5e067-114">Les images clés spline comme <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> créer une transition entre des valeurs en fonction de la valeur de la <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="5e067-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="5e067-115">Dans cet exemple, le rectangle commence par se déplacer lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.</span><span class="sxs-lookup"><span data-stu-id="5e067-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="5e067-116">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="5e067-116">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="5e067-117">Par souci de cohérence avec d’autres exemples d’animation, les versions de code de cet exemple montre comment utilisent un <xref:System.Windows.Media.Animation.Storyboard> objet pour appliquer le <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="5e067-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="5e067-118">Lorsque vous appliquez une animation unique dans le code, il est également plus simple d’utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode au lieu d’utiliser un <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="5e067-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="5e067-119">Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="5e067-119">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e067-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e067-120">See Also</span></span>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [<span data-ttu-id="5e067-121">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="5e067-121">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="5e067-122">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="5e067-122">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
