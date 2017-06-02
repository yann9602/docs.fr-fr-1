---
title: "Fonctions d&#39;acc&#233;l&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "appliquer des formules mathématiques à des animations (WPF)"
  - "appliquer des fonctions d'accélération à des animations (WPF)"
  - "formules mathématiques (WPF), appliquer à des animations"
  - "animations (WPF), mouvement réaliste"
  - "fonctions d'accélération (WPF)"
  - "personnaliser des fonctions d'accélération (WPF)"
  - "fonctions d’accélération (WPF), définition"
  - "fonctions d’accélération (WPF), personnalisation"
  - "appliquer des animations (WPF),"
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Fonctions d&#39;acc&#233;l&#233;ration
Fonctions d’accélération permettent d’appliquer des formules mathématiques personnalisées à vos animations. Par exemple, vous souhaiterez un objet réaliste rebondissent ou se comportent comme si elle se trouvait sur un ressort. Vous pouvez utiliser des images clés ou même des animations From/To/By pour se rapprocher de ces effets, mais cela prendrait beaucoup de travail et l’animation serait moins précise que l’utilisation d’une formule mathématique.  
  
 Outre la création de votre propre fonction d’accélération personnalisée en héritant de <xref:System.Windows.Media.Animation.EasingFunctionBase>, vous pouvez utiliser une des fonctions d’accélération fournies par le runtime pour créer des effets courants.  
  
-   <xref:System.Windows.Media.Animation.BackEase>: rétracte légèrement le mouvement d’une animation avant de commencer à animer dans le chemin d’accès indiqué.  
  
-   <xref:System.Windows.Media.Animation.BounceEase>: crée un effet rebondissant.  
  
-   <xref:System.Windows.Media.Animation.CircleEase>: crée une animation qui accélère et/ou ralentit à l’aide d’une fonction circulaire.  
  
-   <xref:System.Windows.Media.Animation.CubicEase>: crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*( *t*) = *t*<sup>3</sup>.  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>: crée une animation qui ressemble à un ressort OSCILLANT jusqu'à s’arrêter.  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>: crée une animation qui accélère et/ou ralentit à l’aide d’une formule exponentielle.  
  
-   <xref:System.Windows.Media.Animation.PowerEase>: crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*( *t*) = *t*<sup>p</sup> où p est égal à la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriété.  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>: crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*( *t*) = *t*<sup>2</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>: crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*( *t*) = *t*<sup>4</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>: créer une animation qui accélère et/ou ralentit à l’aide de la formule *f*( *t*) = *t*<sup>5</sup>.  
  
-   <xref:System.Windows.Media.Animation.SineEase>: crée une animation qui accélère et/ou ralentit à l’aide d’une formule de sinus.  
  
 Vous pouvez explorer le comportement de ces fonctions d’accélération avec l’exemple suivant.  
  
 [Exécutez cet exemple](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 Pour appliquer une fonction d’accélération à une animation, utilisez le `EasingFunction` propriété de l’animation spécifient la fonction d’accélération à appliquer à l’animation. L’exemple suivant applique un <xref:System.Windows.Media.Animation.BounceEase> fonction d’accélération un <xref:System.Windows.Media.Animation.DoubleAnimation> pour créer un effet rebondissant.  
  
 [Exécutez cet exemple](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 Dans l’exemple précédent, la fonction d’accélération a été appliquée à un From/To/By animation. Vous pouvez également appliquer ces fonctions d’accélération aux animations d’image clé. L’exemple suivant montre comment utiliser des images clés avec les fonctions associées d’accélération pour créer une animation d’un rectangle dont les contrats vers le haut, ralentit, se développe vers le bas (comme si des relevant) puis puis rebondit jusqu'à l’arrêt.  
  
 [Exécutez cet exemple](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Vous pouvez utiliser la <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> propriété pour modifier le comporte la fonction d’accélération, c'est-à-dire, changer l’interpolation de l’animation. Il existe trois valeurs possibles, vous pouvez attribuer aux <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode>: l’Interpolation suit la formule mathématique associée à la fonction d’accélération.  
  
-   <xref:System.Windows.Media.Animation.EasingMode>: l’Interpolation suit 100 % d’interpolation moins le résultat de la formule associée à la fonction d’accélération.  
  
-   <xref:System.Windows.Media.Animation.EasingMode>: l’Interpolation utilise <xref:System.Windows.Media.Animation.EasingMode> pour la première moitié de l’animation et <xref:System.Windows.Media.Animation.EasingMode> pour le deuxième semestre.  
  
 Les graphiques suivants montrent les différentes valeurs de <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> où *f*( *x*) représente la progression de l’animation et *t* représente l’heure.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Graphiques BackEase EasingMode. ] (../Image/BackEase_Graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Graphiques BounceEase EasingMode. ] (../Image/BounceEase_Graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Graphiques CircleEase EasingMode. ] (../Image/CircleEase_Graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Graphiques CubicEase EasingMode. ] (../Image/CubicEase_Graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase avec graphiques de différents easingmodes. ] (../Image/ElasticEase_Graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Graphiques ExponentialEase de différents easingmodes. ] (../Image/ExponentialEase_Graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase avec graphiques de différents easingmodes. ] (../Image/QuarticEase_Graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase avec graphiques de différents easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase avec graphiques de différents easingmodes. ] (../Image/QuarticEase_Graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase avec graphiques de différents easingmodes. ] (../Image/QuinticEase_Graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase pour différentes valeurs EasingMode](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  Vous pouvez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour créer le même comportement que <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, et <xref:System.Windows.Media.Animation.QuinticEase> à l’aide de la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriété. Par exemple, si vous souhaitez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour remplacer les <xref:System.Windows.Media.Animation.CubicEase>, spécifiez un <xref:System.Windows.Media.Animation.PowerEase.Power%2A> la valeur 3.  
  
 Outre l’utilisation des fonctions d’accélération présentes à l’exécution, vous pouvez créer vos propres fonctions d’accélération personnalisées en héritant de <xref:System.Windows.Media.Animation.EasingFunctionBase>. L’exemple suivant montre comment créer une fonction d’accélération personnalisée simple. Vous pouvez ajouter votre propre logique mathématique pour le comporte de la fonction d’accélération en substituant la <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> (méthode).  
  
 [Exécutez cet exemple](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]