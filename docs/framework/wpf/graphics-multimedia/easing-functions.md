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
ms.openlocfilehash: 198ec8b8cb0b27e009f01f8e60a47e8086a7dbc7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="easing-functions"></a>Fonctions d'accélération
Les fonctions d’accélération permettent d’appliquer des formules mathématiques personnalisées à des animations. Par exemple, vous pouvez faire en sorte qu’un objet rebondisse ou se comporte comme s’il était sur un ressort de façon réaliste. On peut utiliser des animations d’images clés ou même From/To/By pour se rapprocher de ces effets, mais cela demanderait beaucoup de travail et l’animation serait moins précise qu’avec une formule mathématique.  
  
 En plus de créer votre propre fonction d’accélération personnalisée en héritant de <xref:System.Windows.Media.Animation.EasingFunctionBase>, vous pouvez utiliser une des fonctions d’accélération fournies par le runtime pour créer des effets courants.  
  
-   <xref:System.Windows.Media.Animation.BackEase>: Rétracte légèrement le mouvement d’une animation avant de commencer à animer dans le chemin d’accès indiqué.  
  
-   <xref:System.Windows.Media.Animation.BounceEase>: Crée un effet en mouvement.  
  
-   <xref:System.Windows.Media.Animation.CircleEase>: Crée une animation qui accélère et/ou ralentit en utilisant une fonction circulaire.  
  
-   <xref:System.Windows.Media.Animation.CubicEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>3</sup>.  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>: Crée une animation qui ressemble à un ressort OSCILLANT jusqu'à ce qu’il s’agit de rest.  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>: Crée une animation qui accélère et/ou ralentit à l’aide d’une formule exponentielle.  
  
-   <xref:System.Windows.Media.Animation.PowerEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>p</sup> où p est égal à la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriété.  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>2</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>4</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>: Permet de créer une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>5</sup>.  
  
-   <xref:System.Windows.Media.Animation.SineEase>: Crée une animation qui accélère et/ou ralentit à l’aide d’une formule de sinus.  
  
 Vous pouvez explorer le comportement de ces fonctions d’accélération avec l’exemple suivant.  
  
 [Exécuter cet exemple](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 Pour appliquer une fonction d’accélération à une animation, utilisez le `EasingFunction` propriété de l’animation spécifier la fonction d’accélération à appliquer à l’animation. L’exemple suivant applique un <xref:System.Windows.Media.Animation.BounceEase> accélération de fonction à un <xref:System.Windows.Media.Animation.DoubleAnimation> pour créer un effet en mouvement.  
  
 [Exécuter cet exemple](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 Dans l’exemple précédent, la fonction d’accélération a été appliquée à une animation From/To/By. Vous pouvez également appliquer ces fonctions d’accélération aux animations d’images clés. L’exemple suivant montre comment utiliser des images clés avec les fonctions d’accélération associées pour créer une animation d’un rectangle qui se contracte vers le haut, ralentit, s’étend vers le bas (comme s’il tombait), puis rebondit jusqu’à s’arrêter.  
  
 [Exécuter cet exemple](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Vous pouvez utiliser le <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> propriété pour modifier la façon dont la fonction d’accélération se comporte, autrement dit, modifiez l’interpolation de l’animation. Il existe trois valeurs possibles, vous pouvez donner de <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: L’interpolation suit la formule mathématique associée à la fonction d’accélération.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: L’interpolation suit 100 % d’interpolation moins le résultat de la formule associée à la fonction d’accélération.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: L’interpolation utilise <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pour la première moitié de l’animation et <xref:System.Windows.Media.Animation.EasingMode.EaseOut> pour la deuxième moitié.  
  
 Les graphiques suivants montrent les différentes valeurs de <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> où *f*(*x*) représente la progression de l’animation et *t* représente l’heure.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Graphiques EasingMode BackEase.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Graphiques EasingMode BounceEase.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Graphiques EasingMode CircleEase.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Graphiques EasingMode CubicEase.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase avec graphiques de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Graphiques ExponentialEase de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase avec graphiques de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase avec graphiques de différents easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase avec graphiques de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase avec graphiques de différents easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase pour différentes valeurs EasingMode](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  Vous pouvez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour créer le même comportement que <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, et <xref:System.Windows.Media.Animation.QuinticEase> à l’aide de la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriété. Par exemple, si vous souhaitez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour remplacer les <xref:System.Windows.Media.Animation.CubicEase>, spécifiez un <xref:System.Windows.Media.Animation.PowerEase.Power%2A> la valeur 3.  
  
 Outre l’utilisation des fonctions d’accélération présentes dans la durée d’exécution, vous pouvez créer vos propres fonctions d’accélération personnalisées en héritant de <xref:System.Windows.Media.Animation.EasingFunctionBase>. L’exemple suivant montre comment créer une fonction d’accélération personnalisée simple. Vous pouvez ajouter votre propre logique mathématique pour le comportement de la fonction d’accélération en substituant la <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> (méthode).  
  
 [Exécuter cet exemple](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
