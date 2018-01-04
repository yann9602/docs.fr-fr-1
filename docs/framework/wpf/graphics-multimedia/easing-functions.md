---
title: "Fonctions d'accélération"
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
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 570a065d3f28befe8db4887ff908c3bd60a639a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="easing-functions"></a><span data-ttu-id="7fb11-102">Fonctions d'accélération</span><span class="sxs-lookup"><span data-stu-id="7fb11-102">Easing Functions</span></span>
<span data-ttu-id="7fb11-103">Les fonctions d’accélération permettent d’appliquer des formules mathématiques personnalisées à des animations.</span><span class="sxs-lookup"><span data-stu-id="7fb11-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="7fb11-104">Par exemple, vous pouvez faire en sorte qu’un objet rebondisse ou se comporte comme s’il était sur un ressort de façon réaliste.</span><span class="sxs-lookup"><span data-stu-id="7fb11-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="7fb11-105">On peut utiliser des animations d’images clés ou même From/To/By pour se rapprocher de ces effets, mais cela demanderait beaucoup de travail et l’animation serait moins précise qu’avec une formule mathématique.</span><span class="sxs-lookup"><span data-stu-id="7fb11-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="7fb11-106">En plus de créer votre propre fonction d’accélération personnalisée en héritant de <xref:System.Windows.Media.Animation.EasingFunctionBase>, vous pouvez utiliser une des fonctions d’accélération fournies par le runtime pour créer des effets courants.</span><span class="sxs-lookup"><span data-stu-id="7fb11-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="7fb11-107"><xref:System.Windows.Media.Animation.BackEase>: Rétracte légèrement le mouvement d’une animation avant de commencer à animer dans le chemin d’accès indiqué.</span><span class="sxs-lookup"><span data-stu-id="7fb11-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="7fb11-108"><xref:System.Windows.Media.Animation.BounceEase>: Crée un effet en mouvement.</span><span class="sxs-lookup"><span data-stu-id="7fb11-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="7fb11-109"><xref:System.Windows.Media.Animation.CircleEase>: Crée une animation qui accélère et/ou ralentit en utilisant une fonction circulaire.</span><span class="sxs-lookup"><span data-stu-id="7fb11-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="7fb11-110"><xref:System.Windows.Media.Animation.CubicEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="7fb11-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="7fb11-111"><xref:System.Windows.Media.Animation.ElasticEase>: Crée une animation qui ressemble à un ressort OSCILLANT jusqu'à ce qu’il s’agit de rest.</span><span class="sxs-lookup"><span data-stu-id="7fb11-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="7fb11-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Crée une animation qui accélère et/ou ralentit à l’aide d’une formule exponentielle.</span><span class="sxs-lookup"><span data-stu-id="7fb11-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="7fb11-113"><xref:System.Windows.Media.Animation.PowerEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>p</sup> où p est égal à la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="7fb11-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="7fb11-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="7fb11-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="7fb11-115"><xref:System.Windows.Media.Animation.QuarticEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="7fb11-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="7fb11-116"><xref:System.Windows.Media.Animation.QuinticEase>: Permet de créer une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="7fb11-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="7fb11-117"><xref:System.Windows.Media.Animation.SineEase>: Crée une animation qui accélère et/ou ralentit à l’aide d’une formule de sinus.</span><span class="sxs-lookup"><span data-stu-id="7fb11-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="7fb11-118">Vous pouvez explorer le comportement de ces fonctions d’accélération avec l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7fb11-118">You can explore the behavior of these easing functions with the following sample.</span></span>  
  
 [<span data-ttu-id="7fb11-119">Exécuter cet exemple</span><span class="sxs-lookup"><span data-stu-id="7fb11-119">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 <span data-ttu-id="7fb11-120">Pour appliquer une fonction d’accélération à une animation, utilisez le `EasingFunction` propriété de l’animation spécifier la fonction d’accélération à appliquer à l’animation.</span><span class="sxs-lookup"><span data-stu-id="7fb11-120">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="7fb11-121">L’exemple suivant applique un <xref:System.Windows.Media.Animation.BounceEase> accélération de fonction à un <xref:System.Windows.Media.Animation.DoubleAnimation> pour créer un effet en mouvement.</span><span class="sxs-lookup"><span data-stu-id="7fb11-121">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [<span data-ttu-id="7fb11-122">Exécuter cet exemple</span><span class="sxs-lookup"><span data-stu-id="7fb11-122">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="7fb11-123">Dans l’exemple précédent, la fonction d’accélération a été appliquée à une animation From/To/By.</span><span class="sxs-lookup"><span data-stu-id="7fb11-123">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="7fb11-124">Vous pouvez également appliquer ces fonctions d’accélération aux animations d’images clés.</span><span class="sxs-lookup"><span data-stu-id="7fb11-124">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="7fb11-125">L’exemple suivant montre comment utiliser des images clés avec les fonctions d’accélération associées pour créer une animation d’un rectangle qui se contracte vers le haut, ralentit, s’étend vers le bas (comme s’il tombait), puis rebondit jusqu’à s’arrêter.</span><span class="sxs-lookup"><span data-stu-id="7fb11-125">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [<span data-ttu-id="7fb11-126">Exécuter cet exemple</span><span class="sxs-lookup"><span data-stu-id="7fb11-126">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="7fb11-127">Vous pouvez utiliser le <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> propriété pour modifier la façon dont la fonction d’accélération se comporte, autrement dit, modifiez l’interpolation de l’animation.</span><span class="sxs-lookup"><span data-stu-id="7fb11-127">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="7fb11-128">Il existe trois valeurs possibles, vous pouvez donner de <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="7fb11-128">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="7fb11-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: L’interpolation suit la formule mathématique associée à la fonction d’accélération.</span><span class="sxs-lookup"><span data-stu-id="7fb11-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="7fb11-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: L’interpolation suit 100 % d’interpolation moins le résultat de la formule associée à la fonction d’accélération.</span><span class="sxs-lookup"><span data-stu-id="7fb11-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="7fb11-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: L’interpolation utilise <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pour la première moitié de l’animation et <xref:System.Windows.Media.Animation.EasingMode.EaseOut> pour la deuxième moitié.</span><span class="sxs-lookup"><span data-stu-id="7fb11-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="7fb11-132">Les graphiques suivants montrent les différentes valeurs de <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> où *f*(*x*) représente la progression de l’animation et *t* représente l’heure.</span><span class="sxs-lookup"><span data-stu-id="7fb11-132">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="7fb11-133">![Graphiques EasingMode BackEase.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-133">![BackEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="7fb11-134">![Graphiques EasingMode BounceEase.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-134">![BounceEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="7fb11-135">![Graphiques EasingMode CircleEase.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-135">![CircleEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="7fb11-136">![Graphiques EasingMode CubicEase.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-136">![CubicEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="7fb11-137">![ElasticEase avec graphiques de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-137">![ElasticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="7fb11-138">![Graphiques ExponentialEase de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-138">![ExponentialEase graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="7fb11-139">![QuarticEase avec graphiques de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-139">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="7fb11-140">![QuadraticEase avec graphiques de différents easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-140">![QuadraticEase with graphs of different easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="7fb11-141">![QuarticEase avec graphiques de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-141">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="7fb11-142">![QuinticEase avec graphiques de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-142">![QuinticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="7fb11-143">![SineEase pour différentes valeurs EasingMode](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="7fb11-143">![SineEase for different EasingMode values](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fb11-144">Vous pouvez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour créer le même comportement que <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, et <xref:System.Windows.Media.Animation.QuinticEase> à l’aide de la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="7fb11-144">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="7fb11-145">Par exemple, si vous souhaitez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour remplacer les <xref:System.Windows.Media.Animation.CubicEase>, spécifiez un <xref:System.Windows.Media.Animation.PowerEase.Power%2A> la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="7fb11-145">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="7fb11-146">Outre l’utilisation des fonctions d’accélération présentes dans la durée d’exécution, vous pouvez créer vos propres fonctions d’accélération personnalisées en héritant de <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="7fb11-146">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="7fb11-147">L’exemple suivant montre comment créer une fonction d’accélération personnalisée simple.</span><span class="sxs-lookup"><span data-stu-id="7fb11-147">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="7fb11-148">Vous pouvez ajouter votre propre logique mathématique pour le comportement de la fonction d’accélération en substituant la <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="7fb11-148">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>  
  
 [<span data-ttu-id="7fb11-149">Exécuter cet exemple</span><span class="sxs-lookup"><span data-stu-id="7fb11-149">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
