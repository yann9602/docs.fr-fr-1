---
title: "Vue d&#39;ensemble des animations d&#39;image cl&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "animation, d'images clés"
  - "images clés (WPF), à propos des animations d'image clé"
  - "valeurs cibles d'animation multiples"
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Vue d&#39;ensemble des animations d&#39;image cl&#233;
Cette rubrique vous initie aux animations d'image clé.  Les animations d'image clé vous permettent d'animer en utilisant plus de deux valeurs cibles et contrôlent la méthode d'interpolation d'une animation.  
  
 Cette rubrique contient les sections suivantes.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [Composants requis](#prerequisites)  
  
-   [Utilisation des animations d'image clé](#keyframeanimations)  
  
-   [Rubriques connexes](#seeAlsoToggle)  
  
<a name="prerequisites"></a>   
## Composants requis  
 Pour comprendre cette vue d'ensemble, vous devez être familiarisé avec les animations et les chronologies [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Pour une présentation des animations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Elle permet également de se familiariser avec les animations From\/To\/By.  Pour plus d'informations, consultez [Vue d'ensemble des animations From\/To\/By](../../../../docs/framework/wpf/graphics-multimedia/from-to-by-animations-overview.md).  
  
<a name="whatisakeyframeanimation"></a>   
## Qu'est\-ce qu'une animation d'image clé ?  
 Comme pour une animation From\/To\/By, une animation d'image clé anime la valeur d'une propriété cible.  Elle crée une transition parmi ses valeurs cibles sur sa <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  Toutefois, bien qu'une animation From\/To\/By crée une transition entre deux valeurs, une animation d'image clé unique peut créer des transitions parmi n'importe quel nombre de valeurs cibles.  Contrairement à une animation From\/To\/By, une animation d'image clé n'a aucune propriété From\/To ou By avec lesquelles définir ses valeurs cibles.  Les valeurs cibles d'une animation d'image clé sont décrites à l'aide d'objets d'images clés \(d'où le terme, « animation d'image clé »\).  Pour spécifier les valeurs cibles de l'animation, créez des objets d'image clé et ajoutez\-les à la collection <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> de l'animation.  Lors de l'exécution de l'animation, celle\-ci passe par les images que vous avez indiquées.  
  
 En plus de prendre en charge plusieurs valeurs cibles, certaines méthodes d'image clé prennent même en charge plusieurs méthodes d'interpolation.  La méthode d'interpolation d'une animation définit la façon dont elle transite d'une valeur à la suivante.  Il existe trois types d'interpolations : l'interpolation [discrète](GTMT), [linéaire](GTMT) et [spline](GTMT).  
  
 Pour animer avec une animation d'image clé, vous devez effectuer les étapes suivantes.  
  
-   Déclarez l'animation et spécifiez sa <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, comme vous le feriez pour une animation from\/to\/by.  
  
-   Pour chaque valeur cible, créez une image clé du type approprié, définissez sa valeur et son <xref:System.Windows.Media.Animation.KeyTime> et ajoutez\-la à la collection <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> de l'animation.  
  
-   Associez l'animation à une propriété, comme vous le feriez pour une animation From\/To\/By.  Pour plus d'informations sur l'application d'une animation à une propriété à l'aide d'une table de montage séquentiel, consultez [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 L'exemple suivant utilise <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> pour animer un élément <xref:System.Windows.Shapes.Rectangle> vers quatre emplacements différents.  
  
 [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]
 [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Tout comme une animation From\/To\/By, une animation d'image clé peut être appliquée à une propriété en utilisant un <xref:System.Windows.Media.Animation.Storyboard> dans le balisage et le code ou en utilisant la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> dans le code.  Vous pouvez également utiliser une animation d'image clé pour créer un <xref:System.Windows.Media.Animation.AnimationClock> et l'appliquer à une ou plusieurs propriétés.  Pour plus d'informations sur les différentes méthodes pour appliquer des animations, consultez [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## Types d'animations d'image clé  
 Étant donné que les animations génèrent des valeurs de propriété, il existe différents types d'animations pour les différents types de propriété.  Pour animer une propriété qui accepte un <xref:System.Double> \(telle que la propriété <xref:System.Windows.FrameworkElement.Width%2A> d'un élément\), utilisez une animation qui produit des valeurs <xref:System.Double>.  Pour animer une propriété qui accepte un <xref:System.Windows.Point>, utilisez une animation qui produit des valeurs <xref:System.Windows.Point>, etc.  
  
 Les classes d'animation d'image clé appartiennent à l'espace de noms <xref:System.Windows.Media.Animation> et obéissent à la convention d'affectation de noms suivante :  
  
 *\<Type\>* `AnimationUsingKeyFrames`  
  
 Où *\<Type\>* est le type de valeur que la classe anime.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les classes d'animation d'image clé suivantes.  
  
|Type de propriété|Classe d'animation from\/to\/by correspondante|Méthodes d'interpolation prises en charge|  
|-----------------------|----------------------------------------------------|-----------------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Discrète|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Discrète|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Discrète|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Discrète|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
  
<a name="animation_target_values"></a>   
## Valeurs cibles \(images clés\) et temps clés  
 De même qu'il existe différents types d'animations d'image clé pour l'animation de différents types de propriété, il y a également différents types d'objets d'image clé : un pour chaque type de valeur animée et pour la méthode d'interpolation prise en charge.  Les types d'image clé obéissent à la convention d'affectation de noms suivante :  
  
 *\<Type\>\<MéthodeInterpolation\>*  `KeyFrame`  
  
 Où *\<MéthodeInterpolation\>* est la méthode d'interpolation qu'utilise l'image clé et *\<Type\>* est le type de valeur que la classe anime.  Une animation d'image clé qui prend en charge les trois méthodes d'interpolation aura trois types d'image clé que vous pouvez utiliser.  Par exemple, vous pouvez utiliser trois types d'image clé avec un <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>et <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>.  \(Les méthodes d'interpolation sont décrites en détail dans une section ultérieure.\)  
  
 L'objectif premier d'une image clé est de spécifier un <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> et une <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  Chaque type d'image clé fournit ces deux propriétés.  
  
-   La propriété <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> spécifie la valeur cible pour cette image clé.  
  
-   La propriété <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> spécifie quand \(dans la <xref:System.Windows.Media.Animation.Timeline.Duration%2A>de l'animation\), la <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> d'une image clé est atteinte.  
  
 Lorsqu'une animation d'image clé commence, elle effectue une itération au sein des images clés dans l'ordre défini par leurs propriétés <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>.  
  
-   S'il n'y a aucune image clé à l'heure 0, l'animation crée une transition entre la valeur actuelle de la propriété cible et la <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> de la première image clé ; sinon, la valeur de sortie de l'animation devient la valeur de la première image clé.  
  
-   L'animation crée une transition entre la <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> de la première et deuxième image clé à l'aide de la méthode d'interpolation spécifiée par la deuxième image clé.  La transition commence au premier <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> de l'image clé et se termine lorsque le deuxième <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> de l'image clé est atteint.  
  
-   L'animation continue, créant des transitions entre chaque image clé suivante et son image clé précédente.  
  
-   Enfin, l'animation passe à la valeur de l'image clé avec le plus grand temps clé égal ou inférieur à la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de l'animation.  
  
 Si la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de l'animation est <xref:System.Windows.Duration.Automatic%2A> ou si sa <xref:System.Windows.Media.Animation.Timeline.Duration%2A> est égale au temps de la dernière image clé, l'animation se termine.  Sinon, si la <xref:System.Windows.Duration> de l'animation est supérieure au temps clé de la dernière image clé, l'animation maintient la valeur de l'image clé jusqu'à ce qu'elle atteigne la fin de sa <xref:System.Windows.Duration>.  Comme toutes les animations, une animation d'image clé utilise sa propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pour déterminer si elle maintient sa dernière valeur lorsqu'elle atteint la fin de sa période active.  Pour plus d'informations, consultez [Vue d'ensemble des comportements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
 L'exemple suivant utilise l'objet <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> défini dans l'exemple précédent pour montrer comment fonctionnent les propriétés <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> et <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>.  
  
-   La première image clé affecte immédiatement 0 à la valeur de sortie de l'animation.  
  
-   La deuxième image clé s'anime de 0 à 350.  Elle démarre après la fin de la premier image clé \(à l'heure \= 0 seconde\) et est lue pendant 2 secondes, en terminant à l'heure \= 0:0:2.  
  
-   La troisième image clé s'anime de 350 à 50.  Elle démarre à la fin de la deuxième image clé \(à l'heure \= 2 secondes\) et est lue pendant 5 secondes, en terminant à l'heure \= 0:0:7.  
  
-   La quatrième image clé s'anime de 50 à 200.  Elle démarre à la fin de la troisième image clé \(à l'heure \= 7 secondes\) et est lue pendant 1 seconde, en terminant à l'heure \= 0:0:8.  
  
-   Parce que la valeur 10 secondes a été affectée à la propriété <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de l'animation, l'animation maintient sa dernière valeur pendant deux secondes avant de terminer à \= 0:0:10.  
  
 [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]
 [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## Méthodes d'interpolation  
 Les sections précédentes mentionnent que certaines animations d'image clé prennent en charge plusieurs méthodes d'interpolation.  L'interpolation d'une animation décrit comment une animation transite entre les valeurs sur sa durée.  En sélectionnant le type d'image clé que vous utilisez avec votre animation, vous pouvez définir la méthode d'interpolation pour ce segment d'image clé.  Il existe trois types de méthodes d'interpolation différents : l'interpolation linéaire, discrète et spline.  
  
### Interpolation linéaire  
 Avec l'[interpolation linéaire](GTMT), l'animation progresse à une fréquence d'interpolation constante de la durée du segment.  Par exemple, si un segment de l'image clé passe de 0 à 10 sur une durée de 5 secondes, l'animation aura pour résultat les valeurs suivantes aux temps spécifiés :  
  
|Heure|Valeur de sortie|  
|-----------|----------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### Interpolation discrète  
 Avec l'[interpolation discrète](GTMT), la fonction d'animation passe d'une valeur à la suivante sans interpolation.  Si un segment de l'image clé passe de 0 à 10 sur une durée de 5 secondes, l'animation aura pour résultat les valeurs suivantes aux temps spécifiés :  
  
|Heure|Valeur de sortie|  
|-----------|----------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 Notez la façon dont l'animation ne change pas sa valeur de sortie jusqu'à la fin de la durée du segment.  
  
 L'[interpolation spline](GTMT) est plus complexe.  Elle est décrite dans la section suivante.  
  
<a name="anim_spline"></a>   
### Interpolation spline  
 L'interpolation spline peut être utilisée pour accomplir des effets de minutage plus proches de la réalité.  Parce que les animations sont si souvent utilisées pour imiter des effets qui se produisent dans la réalité, les développeurs peuvent avoir besoin d'un contrôle précis de l'accélération et de la décélération des objets et d'une manipulation au plus près des segments de minutage.  Les images clés de spline vous permettent d'effectuer une animation avec l'interpolation spline.  Avec d'autres images clés, vous spécifiez une <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> et un <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>.  Avec une image clé de spline, vous spécifiez également un <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>.  L'exemple suivant illustre une image clé de spline unique pour une <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  Remarquez la propriété <xref:System.Windows.Media.Animation.KeySpline> ; c'est ce qui rend une image clé de spline différente des autres types d'images clés.  
  
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Une [courbe de Bézier cubique](GTMT) est définie par un point de départ, un point de fin et deux points de contrôle.  La propriété <xref:System.Windows.Media.Animation.KeySpline> d'une image clé de spline définit les deux points de contrôle d'une courbe de Bézier qui s'étend de \(0,0\) à \(1,1\).  Le premier point de contrôle contrôle le facteur de courbe de la première moitié de la courbe de Bézier, et le deuxième contrôle le facteur de courbe de la seconde moitié de la courbe de Bézier.  La courbe résultante décrit le taux de changement pour cette image clé de spline.  Plus la courbe est raide, plus l'image clé modifie rapidement ses valeurs.  Lorsque la courbe s'aplatit, l'image clé modifie ses valeurs plus lentement.  
  
 Vous pouvez utiliser <xref:System.Windows.Media.Animation.KeySpline> pour simuler des trajectoires physiques comme des chutes d'eau ou des balles en mouvement ou appliquer d'autres effets d'« atténuation \+ » ou d'« atténuation – » pour mettre les animations en mouvement.  Pour les effets d'intervention de l'utilisateur comme les atténuations d'arrière\-plan ou le rebond du bouton de contrôle, vous pouvez appliquer l'interpolation spline pour accélérer ou ralentir le taux de changement d'une animation d'une façon spécifique.  
  
 L'exemple suivant spécifie un <xref:System.Windows.Media.Animation.KeySpline> de 0,1 1,0, qui crée la courbe de Bézier suivante.  
  
 ![Courbe de Bézier](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm\_keyspline\_0\_1\_1\_0")  
Spline clé avec les points de contrôle \(0.0, 1.0\) et \(1.0, 0.0\)  
  
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Cette image clé s'anime rapidement lorsqu'elle commence, ralentit, puis accélère à nouveau avant qu'elle ne se termine.  
  
 L'exemple suivant spécifie un <xref:System.Windows.Media.Animation.KeySpline> de 0.5,0.25 0.75,1.0, qui crée la courbe de Bézier suivante.  
  
 ![Courbe de Bézier](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm\_keyspline\_025\_050\_075\_10")  
Spline clé avec les points de contrôle \(0.25, 0.5\) et \(0.75, 1.0\)  
  
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Parce que la courbure de la courbe de Bézier change très peu, cette image clé s'anime à une fréquence presque constante ; elle ralentit quelque peu vers la fin.  
  
 L'exemple suivant utilise <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> pour animer la position du rectangle.  Comme <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> utilise des objets <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>, la transition entre chaque valeur d'image clé utilise l'interpolation spline.  
  
 [!code-xml[keyframes_ovw_snip#SplinedInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]
 [!code-xml[keyframes_ovw_snip#SplinedInterpolationExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 L'interpolation spline peut être difficile à comprendre ; des essais avec les différents paramètres peuvent vous aider.  [Animation de spline clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160011) vous permet de modifier les valeurs de la spline clé et de voir son résultat dans une animation.  
  
<a name="combininginterpolationmethods"></a>   
### Combinaison des méthodes d'interpolation  
 Vous pouvez utiliser des images clés avec des types d'interpolation différents dans une animation d'image clé unique.  Lorsque deux animations d'image clé avec des interpolations différentes se suivent, la méthode d'interpolation de la deuxième image clé est utilisée pour créer la transition de la première valeur vers la seconde.  
  
 Dans l'exemple suivant, <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> est créé qui utilise une interpolation linéaire, spline et discrète.  
  
 [!code-xml[keyframes_ovw_snip#ComboInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]
 [!code-xml[keyframes_ovw_snip#ComboInterpolationExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## En savoir plus sur la durée et les temps clés  
 Comme les autres animations, les animations d'image clé ont une propriété <xref:System.Windows.Duration>.  En plus de spécifier la <xref:System.Windows.Duration> de l'animation, vous devez spécifier la partie de cette durée qui sera donnée à chaque image clé.  Pour ce faire, décrivez un   <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> pour chacune des images clés de l'animation.  Le <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> de chaque image clé indique le délai au bout duquel elle arrive à son terme.  
  
 La propriété du <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ne spécifie pas combien de temps dure la lecture du temps clé.  La durée de lecture d'une image clé est déterminée par le moment où se termine l'image clé, le moment où se termine l'image clé qui la précède ainsi que par la durée de l'animation.  Les temps clés peuvent être spécifiés comme une valeur d'heure, un pourcentage ou comme les valeurs spéciales <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> ou <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 La liste suivante décrit les différentes façons de spécifier des temps clés.  
  
### Valeurs TimeSpan  
 Vous pouvez utiliser des valeurs <xref:System.TimeSpan> pour spécifier un <xref:System.Windows.Media.Animation.KeyTime>.  La valeur doit être supérieure ou égale à 0 et inférieure ou égale à la durée de l'animation.  L'exemple suivant illustre une animation avec une durée de 10 secondes et quatre images clés dont les temps clés sont spécifiés comme des valeurs d'heure.  
  
-   La première image clé s'anime de la valeur de base à 100 pendant les 3 premières secondes, se terminant à l'heure \= 0:0:03.  
  
-   La deuxième image clé s'anime de 100 à 200.  Elle démarre après la fin de la premier image clé \(à l'heure \= 3 secondes\) et est lue pendant 5 secondes, en terminant à l'heure \= 0:0:8.  
  
-   La troisième image clé s'anime de 200 à 500.  Elle démarre à la fin de la deuxième image clé \(à l'heure \= 8 secondes\) et est lue pendant 1 seconde, en terminant à l'heure \= 0:0:9.  
  
-   La quatrième image clé s'anime de 500 à 600.  Elle démarre à la fin de la troisième image clé \(à l'heure \= 9 secondes\) et est lue pendant 1 seconde, en terminant à l'heure \= 0:0:10.  
  
 [!code-xml[keyframes_ovw_snip#TimeSpanKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#timespankeytimeexample)]
 [!code-xml[keyframes_ovw_snip#TimeSpanKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### Valeurs de pourcentage  
 Une valeur de pourcentage spécifie que l'image clé se termine à un pourcentage de la <xref:System.Windows.Media.Animation.Timeline.Duration%2A>de l'animation.  En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous devez spécifier le pourcentage sous forme de nombre suivi du symbole `%`.  Dans le code, utilisez la méthode <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> et passez\-lui une valeur <xref:System.Double> qui indique le pourcentage.  La valeur doit être supérieure ou égale à 0 et inférieure ou égale à 100 %.  L'exemple suivant illustre une animation avec une durée de 10 secondes et quatre images clés dont les temps clés sont spécifiés comme des pourcentages.  
  
-   La première image clé s'anime de la valeur de base à 100 pendant les 3 premières secondes, se terminant à l'heure \= 0:0:3.  
  
-   La deuxième image clé s'anime de 100 à 200.  Elle démarre après la fin de la premier image clé \(à l'heure \= 3 secondes\) et est lue pendant 5 secondes, en terminant à l'heure \= 0:0:8 \(0.8 x 10 \= 8\).  
  
-   La troisième image clé s'anime de 200 à 500.  Elle démarre à la fin de la deuxième image clé \(à l'heure \= 8 secondes\) et est lue pendant 1 seconde, en terminant à l'heure 0:0:9 \(0.9 x 10 \= 9\).  
  
-   La quatrième image clé s'anime de 500 à 600.  Elle démarre à la fin de la troisième image clé \(à l'heure \= 9 secondes\) et est lue pendant 1 seconde, en terminant à l'heure \= 0:0:10 \(1 x 10 \= 10\).  
  
 [!code-xml[keyframes_ovw_snip#PercentageKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#percentagekeytimeexample)]
 [!code-xml[keyframes_ovw_snip#PercentageKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### Valeur spéciale, Uniform  
 Utilisez la minuterie <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> lorsque vous souhaitez que les images clés aient toutes la même durée.  
  
 Un temps clé <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> divise le temps disponible équitablement par le nombre d'images clés pour déterminer l'heure de fin de chaque image clé.  L'exemple suivant illustre une animation avec une durée de 10 secondes et quatre images clés dont les temps clés sont spécifiés comme <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>.  
  
-   La première image clé s'anime de la valeur de base à 100 pendant les 2,5 premières secondes, se terminant à l'heure \= 0:0:2,5.  
  
-   La deuxième image clé s'anime de 100 à 200.  Elle démarre après la fin de la premier image clé \(à l'heure \= 2.5 secondes\) et est lue pendant environ 2.5 secondes, en terminant à l'heure \= 0:0:5.  
  
-   La troisième image clé s'anime de 200 à 500.  Elle démarre à la fin de la deuxième image clé \(à l'heure \= 5 secondes\) et est lue pendant 2.5 secondes, en terminant à l'heure \= 0:0:7.5.  
  
-   La quatrième image clé s'anime de 500 à 600.  Elle démarre à la fin de la deuxième image clé \(à l'heure \= 7.5 secondes\) et est lue pendant 2.5 secondes, en terminant à l'heure \= 0:0:1.  
  
 [!code-xml[keyframes_ovw_snip#UniformKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#uniformkeytimeexample)]
 [!code-xml[keyframes_ovw_snip#UniformKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### Valeur spéciale, Paced  
 Utilisez la minuterie <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> lorsque vous souhaitez animer à une fréquence constante.  
  
 Un temps clé <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> alloue le temps disponible d'après la longueur de chacune des images clés pour déterminer la durée de chaque image.  Cela garantit le déroulement à allure constante de l'animation.  L'exemple suivant illustre une animation avec une durée de 10 secondes et trois images clés dont les temps clés sont spécifiés comme <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 [!code-xml[keyframes_ovw_snip#PacedKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#pacedkeytimeexample)]
 [!code-xml[keyframes_ovw_snip#PacedKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Notez que, si le dernier temps clé de l'image clé est <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> ou <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>, son temps clé résolu aura la valeur 100 %.  Si la première image clé dans une animation à plusieurs images est rythmée, son temps clé résolu aura la valeur 0.  \(Si la collection d'images clé contient uniquement une image clé unique qui est rythmée, son temps clé résolu aura la valeur 100 %.\)  
  
 Des images clés différentes dans une animation d'image clé unique peuvent utiliser des temps clés différents.  
  
<a name="combiningkeytimes"></a>   
## Combinaison de temps clés, images clés désordonnées  
 Vous pouvez utiliser des images clés avec des types valeur <xref:System.Windows.Media.Animation.KeyTime> différentes dans la même animation.  Et, bien qu'il soit recommandé d'ajouter les images clés dans l'ordre de leur lecture, ceci n'est pas une obligation.  L'animation et le système de minuterie sont capables de résoudre des images clés désordonnées.  Les images clés avec des temps clés non valides sont ignorées.  
  
 La liste suivante décrit le processus par lequel les temps clés sont résolus pour les images clés d'une animation d'image clé.  
  
1.  Résolvez des valeurs <xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>.  
  
2.  Déterminez la *durée totale de l'interpolation* de l'animation, la durée totale nécessaire à l'animation d'image clé pour compléter une itération avancée.  
  
    1.  Si la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de l'animation n'est pas <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>, la durée totale de l'interpolation est la valeur de la propriété <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de l'animation.  
  
    2.  Sinon, la durée totale de l'interpolation correspond à la plus grande valeur <xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>spécifiée parmi ses images clés, le cas échéant.  
  
    3.  Sinon, la durée totale de l'interpolation est de 1 seconde.  
  
3.  Utilisez la valeur de la durée totale de l'interpolation pour résoudre des valeurs <xref:System.Windows.Media.Animation.KeyTimeType><xref:System.Windows.Media.Animation.KeyTime>.  
  
4.  Résolvez la dernière image clé, si celle\-ci n'a pas déjà été résolue lors des étapes précédentes.  Si le <xref:System.Windows.Media.Animation.KeyTime> de la dernière image clé est <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> ou <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, sa durée résolue sera égale à la durée totale de l'interpolation.  
  
     Si le <xref:System.Windows.Media.Animation.KeyTime> de la première image clé est <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> et que cette animation contient plusieurs images clés, résolvez sa valeur <xref:System.Windows.Media.Animation.KeyTime> à zéro ; s'il existe une seule image clé et que sa valeur <xref:System.Windows.Media.Animation.KeyTime> est <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, elle est résolue à la durée totale de l'interpolation, comme décrit dans l'étape précédente.  
  
5.  Résolvez les valeurs <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime> restantes : elles reçoivent chacune une part égale du temps disponible.  Au cours de ce processus, les valeurs <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> non résolues sont traitées temporairement comme des valeurs <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime> et obtiennent une heure résolue temporaire.  
  
6.  Résolvez les valeurs <xref:System.Windows.Media.Animation.KeyTime> d'images clés avec des temps clés non spécifiés à l'aide des images clés déclarées les plus proches d'elles avec des valeurs <xref:System.Windows.Media.Animation.KeyTime> résolues.  
  
7.  Résolvez les valeurs <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> restantes.  <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>utilisent les valeurs <xref:System.Windows.Media.Animation.KeyTime> des images clés avoisinantes pour déterminer leur heure résolue.  L'objectif est de garantir le déroulement à allure constante de l'animation autour de l'heure résolue de cette image clé.  
  
8.  Triez les images clés par ordre d'heure résolue \(clé primaire\) et ordre de déclaration \(clé secondaire\), c'est\-à\-dire utilisez un tri stable basé sur les valeurs <xref:System.Windows.Media.Animation.KeyTime> de l'image clé résolue.  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.KeyTime>   
 <xref:System.Windows.Media.Animation.KeySpline>   
 <xref:System.Windows.Media.Animation.Timeline>   
 [Animation de spline clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160011)   
 [Animation d'image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [Rubriques "Comment" relatives aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)   
 [Vue d'ensemble des comportements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)