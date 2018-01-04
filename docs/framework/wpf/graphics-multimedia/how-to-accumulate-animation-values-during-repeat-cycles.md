---
title: "Comment : accumuler des valeurs d'animation pendant des cycles de répétition"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a91856cdfcf1ca7ae87e8e571306170feecb7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="0f5d8-102">Comment : accumuler des valeurs d'animation pendant des cycles de répétition</span><span class="sxs-lookup"><span data-stu-id="0f5d8-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="0f5d8-103">Cet exemple montre comment utiliser le <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriété à accumuler des valeurs d’animation sur des cycles de répétition.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f5d8-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="0f5d8-104">Example</span></span>  
 <span data-ttu-id="0f5d8-105">Utilisez le <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriété à accumuler des valeurs de base d’une animation sur des cycles de répétition.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="0f5d8-106">Par exemple, si vous définissez une animation à répéter 9 heures (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = « 9 x ») et que vous définissez la propriété à animer entre 10 et 15 (de = 10 à = 15), la propriété s’anime de 10 à 15 pendant le premier cycle, de 15 à 20 pendant le deuxième cycle , de 20 à 25 pendant le troisième cycle et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="0f5d8-107">Par conséquent, chaque cycle d’animation utilise la valeur finale de l’animation à partir du cycle d’animation précédent comme valeur de base.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="0f5d8-108">Vous pouvez utiliser le `IsCumulative` propriété avec des animations plus simples et la plupart des animations d’image clé.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="0f5d8-109">Pour plus d’informations, consultez [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) et [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f5d8-109">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="0f5d8-110">L’exemple suivant illustre ce comportement par l’animation de la largeur de quatre rectangles.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="0f5d8-111">L’exemple :</span><span class="sxs-lookup"><span data-stu-id="0f5d8-111">The example:</span></span>  
  
-   <span data-ttu-id="0f5d8-112">Anime le premier rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimation> et définit les <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="0f5d8-113">Anime le deuxième rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimation> et définit les <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriété à la valeur par défaut de `false`.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
-   <span data-ttu-id="0f5d8-114">Anime le troisième rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> et définit les <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="0f5d8-115">Anime le dernier rectangle avec <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> et définit les <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="0f5d8-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0f5d8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f5d8-116">See Also</span></span>  
 [<span data-ttu-id="0f5d8-117">Ajouter une valeur de sortie d'animation à une valeur de départ d'animation</span><span class="sxs-lookup"><span data-stu-id="0f5d8-117">Add an Animation Output Value to an Animation Starting Value</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [<span data-ttu-id="0f5d8-118">Répéter une animation</span><span class="sxs-lookup"><span data-stu-id="0f5d8-118">Repeat an Animation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [<span data-ttu-id="0f5d8-119">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="0f5d8-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="0f5d8-120">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="0f5d8-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="0f5d8-121">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="0f5d8-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
