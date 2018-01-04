---
title: "Comment : animer une rotation 3D à l'aide d'images clés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca1b49277792e89f1d0cc7ca213d02978bb4dee3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="a5b0e-102">Comment : animer une rotation 3D à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="a5b0e-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="a5b0e-103">Dans l’exemple suivant, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> est utilisé pour faire pivoter pendant que son axe de rotation s’anime en créant une « déviation » un objet en 3D.</span><span class="sxs-lookup"><span data-stu-id="a5b0e-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="a5b0e-104">Cette animation utilise les images clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a5b0e-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="a5b0e-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>permet de créer une interpolation linéaire entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="a5b0e-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="a5b0e-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>permet de créer des « sauts » soudains entre les valeurs (aucune interpolation).</span><span class="sxs-lookup"><span data-stu-id="a5b0e-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="a5b0e-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>permet de créer une transition entre des valeurs en fonction de la <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="a5b0e-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="a5b0e-108">Dans l’exemple ci-dessous, cette partie de l’animation commence lentement vers la fin du segment temporel, accélère de façon exponentielle.</span><span class="sxs-lookup"><span data-stu-id="a5b0e-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5b0e-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5b0e-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a5b0e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5b0e-110">See Also</span></span>  
 [<span data-ttu-id="a5b0e-111">Vue d’ensemble des graphiques 3D</span><span class="sxs-lookup"><span data-stu-id="a5b0e-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="a5b0e-112">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="a5b0e-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="a5b0e-113">Animer une rotation 3D à l’aide de storyboards</span><span class="sxs-lookup"><span data-stu-id="a5b0e-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="a5b0e-114">Animer une rotation 3D à l’aide de Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="a5b0e-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="a5b0e-115">Animer une rotation 3D à l'aide de quaternions</span><span class="sxs-lookup"><span data-stu-id="a5b0e-115">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="a5b0e-116">Animer une rotation 3D à l’aide d’images clés (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="a5b0e-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
