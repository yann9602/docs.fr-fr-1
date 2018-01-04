---
title: "Comment : ajouter une valeur de sortie d'animation à une valeur de départ d'animation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1a6a5923655c5857b813df778b36b6c7fd208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="a0fc3-102">Comment : ajouter une valeur de sortie d'animation à une valeur de départ d'animation</span><span class="sxs-lookup"><span data-stu-id="a0fc3-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="a0fc3-103">Cet exemple montre comment ajouter une valeur de sortie de l’animation à une valeur de départ de l’animation.</span><span class="sxs-lookup"><span data-stu-id="a0fc3-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0fc3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a0fc3-104">Example</span></span>  
 <span data-ttu-id="a0fc3-105">Le <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> propriété spécifie si vous souhaitez que la valeur de sortie d’une animation ajoutée à la valeur de départ (valeur de base) d’une propriété animée.</span><span class="sxs-lookup"><span data-stu-id="a0fc3-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="a0fc3-106">Vous pouvez utiliser le <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> propriété avec des animations plus simples et la plupart des animations d’image clé.</span><span class="sxs-lookup"><span data-stu-id="a0fc3-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="a0fc3-107">Pour plus d’informations, consultez [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) et [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a0fc3-107">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="a0fc3-108">L’exemple suivant montre l’effet de l’utilisation de la <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> propriété avec <xref:System.Windows.Media.Animation.DoubleAnimation> et à l’aide de la <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> propriété avec <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="a0fc3-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a0fc3-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0fc3-109">See Also</span></span>  
 [<span data-ttu-id="a0fc3-110">Accumuler des valeurs d'animation pendant des cycles de répétition</span><span class="sxs-lookup"><span data-stu-id="a0fc3-110">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="a0fc3-111">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="a0fc3-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a0fc3-112">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="a0fc3-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="a0fc3-113">Animation et minutage</span><span class="sxs-lookup"><span data-stu-id="a0fc3-113">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="a0fc3-114">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="a0fc3-114">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
