---
title: "Comment : animer des modifications de taille à l'aide d'images clés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9577f9f08fa1d19aa214bda5a1aef997c2cfa2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="741e8-102">Comment : animer des modifications de taille à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="741e8-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="741e8-103">Cet exemple explique comment animer des modifications de taille à l’aide d’images clés.</span><span class="sxs-lookup"><span data-stu-id="741e8-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="741e8-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="741e8-104">Example</span></span>  
 <span data-ttu-id="741e8-105">L’exemple suivant utilise le <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> classe pour animer la <xref:System.Windows.Media.ArcSegment.Size%2A> propriété d’un <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="741e8-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="741e8-106">Cette animation utilise trois images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="741e8-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="741e8-107">Pendant la première demi-seconde de l’animation, utilise une instance de la <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> classe pour augmenter progressivement la taille de l’arc. Images clés linéaires comme <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> créer une transition linéaire fluide entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="741e8-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="741e8-108">À la fin de la prochaine demi-seconde, utilise une instance de la <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> classe soudainement augmenter la taille de l’arc. Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> créer soudains entre les valeurs, autrement dit, les modifications de taille se produisent soudainement et ne sont pas subtiles.</span><span class="sxs-lookup"><span data-stu-id="741e8-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3.  <span data-ttu-id="741e8-109">Sur les deux dernières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> classe pour augmenter la taille de l’arc. Les images clés spline comme <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> créer une transition entre des valeurs en fonction des valeurs de la <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="741e8-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="741e8-110">Dans cet exemple, la taille de l’arc augmente lentement dans un premier temps, puis augmente de façon exponentielle vers la fin du segment temporel.</span><span class="sxs-lookup"><span data-stu-id="741e8-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="741e8-111">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="741e8-111">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="741e8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="741e8-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [<span data-ttu-id="741e8-113">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="741e8-113">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="741e8-114">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="741e8-114">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
