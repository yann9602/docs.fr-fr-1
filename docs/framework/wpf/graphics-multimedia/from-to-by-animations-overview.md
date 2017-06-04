---
title: "Vue d&#39;ensemble des animations From/To/By | Microsoft Docs"
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
  - "animation, From/To/By"
  - "From/To/By (animation)"
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Vue d&#39;ensemble des animations From/To/By
Cette rubrique explique comment utiliser des animations From\/To\/By pour animer des [propriétés de dépendance](GTMT).  Une animation From\/To\/By crée une transition entre deux valeurs.  
  
 Cette rubrique contient les sections suivantes.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prereq"></a>   
## Composants requis  
 Pour comprendre cette rubrique, vous devez être familiarisé avec les fonctionnalités d'animations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Pour une introduction aux fonctionnalités d'animation, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="whatisanimation"></a>   
## Qu'est\-ce qu'une animation From\/To\/By ?  
 Une animation From\/To\/By est un type d'<xref:System.Windows.Media.Animation.AnimationTimeline> qui crée une transition entre une valeur initiale et une valeur finale.  Le temps nécessaire pour que la transition se termine est déterminé par la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cette animation.  
  
 Vous pouvez appliquer une animation From\/To\/By à une propriété en utilisant un <xref:System.Windows.Media.Animation.Storyboard> dans le balisage et le code, ou en utilisant la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> dans le code.  Vous pouvez également utiliser une animation From\/To\/By pour créer un <xref:System.Windows.Media.Animation.AnimationClock> et l'appliquer à une ou plusieurs propriétés.  Pour plus d'informations sur les différentes méthodes pour appliquer des animations, consultez [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
 Les animations From\/To\/By ne peuvent pas compter plus de deux valeurs cibles.  Si vous avez besoin d'une animation comptant plus de deux valeurs cibles, utilisez une animation d'image clé.  Les animations d'image clé sont décrites dans [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## Types d'animations From\/To\/By  
 Étant donné que les animations génèrent des valeurs de propriété, il existe différents types d'animations pour les différents types de propriété.  Pour animer une propriété qui accepte un <xref:System.Double>, telle que la propriété <xref:System.Windows.FrameworkElement.Width%2A> d'un élément, utilisez une animation qui produit des valeurs <xref:System.Double>.  Pour animer une propriété qui accepte un <xref:System.Windows.Point>, utilisez une animation qui produit des valeurs <xref:System.Windows.Point>, etc.  
  
 Les classes d'animation From\/To\/By appartiennent à l'espace de noms <xref:System.Windows.Media.Animation> et utilisent la convention d'affectation de noms suivante :  
  
 *\<Type\>* `Animation`  
  
 Où *\<Type\>* est le type de valeur que la classe anime.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les classes d'animation From\/To\/By suivantes.  
  
|Type de propriété|Classe d'animation From\/To\/By correspondante|  
|-----------------------|----------------------------------------------------|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimation>|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimation>|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16Animation>|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32Animation>|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64Animation>|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimation>|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimation>|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimation>|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimation>|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimation>|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimation>|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimation>|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimation>|  
  
<a name="anim_values"></a>   
## Valeurs cibles  
 Une animation From\/To\/By crée une transition entre deux valeurs cibles.  Il est courant de spécifier une valeur initiale \(définissez\-la en utilisant la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>\) et une valeur finale \(définissez\-la en utilisant la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>\).  Toutefois, vous pouvez également spécifier uniquement une valeur initiale, une valeur de destination ou une valeur de décalage.  Dans ces cas, l'animation obtient la valeur cible manquante de la propriété qui est animée.  La liste suivante décrit les différentes manières de spécifier les valeurs cibles d'une animation.  
  
-   **Valeur initiale**  
  
     Utilisez la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> lorsque vous souhaitez spécifier explicitement la valeur initiale d'une animation.  Vous pouvez utiliser la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> seule, ou avec la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ou <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  Si vous spécifiez uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, l'animation effectue la transition de cette valeur à la valeur de base de la propriété animée.  
  
-   **Valeur finale**  
  
     Pour spécifier la valeur finale d'une animation, utilisez sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  Si vous utilisez la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> seule, l'animation obtient sa valeur initiale à partir de la propriété qui est animée ou à partir de la sortie d'une autre animation appliquée à la même propriété.  Vous pouvez utiliser la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> avec la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> afin de spécifier explicitement des valeurs initiales et finales pour l'animation.  
  
-   **Valeur de décalage**  
  
     La propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vous permet de spécifier un offset au lieu d'une valeur initiale ou finale explicite pour l'animation.  La propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> d'une animation spécifie de combien l'animation modifie une valeur sur sa durée.  Vous pouvez utiliser la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> seule ou avec la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>.  Si vous spécifiez uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, l'animation ajoute la valeur de décalage à la valeur de base de la propriété ou à la sortie d'une autre animation.  
  
<a name="examples"></a>   
## Utilisation des valeurs From\/To\/By  
 Les sections suivantes décrivent comment utiliser ensemble ou séparément les propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 Les exemples de cette section utilisent chacun un <xref:System.Windows.Media.Animation.DoubleAnimation> qui est un type d'animation From\/To\/By, pour animer la propriété <xref:System.Windows.FrameworkElement.Width%2A> d'un <xref:System.Windows.Shapes.Rectangle> qui fait 10 [pixels indépendants du périphérique](GTMT) de haut et 100 [pixels indépendants du périphérique](GTMT) de large.  
  
 Bien que chaque exemple utilise un <xref:System.Windows.Media.Animation.DoubleAnimation>, les propriétés De, À et Par de toutes les animations From\/To\/By se comportent de la même manière.  Bien que chacun de ces exemples utilise un <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez utiliser les animations From\/To\/By de manière différente.  Pour plus d'informations, consultez [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### De\/À  
 Lorsque vous définissez ensemble les valeurs <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, l'animation passe de la valeur qui est spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> à la valeur qui est spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 L'exemple suivant affecte à la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> du <xref:System.Windows.Media.Animation.DoubleAnimation> la valeur 50 et à sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> la valeur 300.  Par conséquent, le <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animé de 50 à 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### Pour  
 Lorsque vous définissez uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, l'animation passe de la valeur de base de la propriété animée, ou de la sortie d'une animation de composition qui a été appliquée précédemment à la même propriété, à la valeur qui est spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 \(Le terme « animation de composition » fait référence à une animation <xref:System.Windows.Media.Animation.ClockState> ou <xref:System.Windows.Media.Animation.ClockState> qui s'appliquait précédemment à la même propriété, qui est encore appliquée, lors de l'application de l'animation actuelle à l'aide du comportement de transfert de travail <xref:System.Windows.Media.Animation.HandoffBehavior>.\)  
  
 L'exemple suivant affecte uniquement à la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> de <xref:System.Windows.Media.Animation.DoubleAnimation> la valeur 300.  Étant donné qu'aucune valeur de départ n'a été spécifiée, le <xref:System.Windows.Media.Animation.DoubleAnimation> utilise la valeur de base \(100\) de la propriété <xref:System.Windows.FrameworkElement.Width%2A> comme valeur de départ.  La <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animée de 100 à la valeur cible de l'animation qui est de 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### Par  
 Lorsque vous définissez uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>d'une animation, celle\-ci passe de la valeur de base de la propriété animée, ou de la sortie d'une animation de composition, à la somme de cette valeur et de la valeur qui est spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 L'exemple suivant affecte uniquement à la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de <xref:System.Windows.Media.Animation.DoubleAnimation> la valeur 300.  Étant donné que l'exemple ne spécifie pas de valeur de départ, le <xref:System.Windows.Media.Animation.DoubleAnimation> utilise la valeur de base de la propriété <xref:System.Windows.FrameworkElement.Width%2A>, à savoir 100, comme valeur de départ.  La valeur finale est déterminée en ajoutant la valeur <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de l'animation, à savoir 300, à sa valeur initiale, qui est 100 : 400  Par conséquent, le <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animé de 100 à 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### De\/Par  
 Lorsque vous définissez les propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> d'une animation, celle\-ci passe de la valeur qui est spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> à la valeur qui est spécifiée par la somme des propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 L'exemple suivant affecte à la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> du <xref:System.Windows.Media.Animation.DoubleAnimation> la valeur 50 et à sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> la valeur 300.  La valeur finale est déterminée en ajoutant la valeur <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de l'animation, à savoir 300, à sa valeur initiale, qui est 50 : 350  Par conséquent, le <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animé de 50 à 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### From  
 Lorsque vous spécifiez uniquement la valeur <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> d'une animation, celle\-ci passe de la valeur qui est spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> à la valeur de base de la propriété qui est animée ou à la sortie d'une animation de composition.  
  
 L'exemple suivant affecte uniquement à la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> de <xref:System.Windows.Media.Animation.DoubleAnimation> la valeur 50.  Étant donné qu'aucune valeur finale n'a été spécifiée, le <xref:System.Windows.Media.Animation.DoubleAnimation> utilise la valeur de base de la propriété <xref:System.Windows.FrameworkElement.Width%2A>, à savoir 100, comme valeur finale.  La <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animée de 50 à la valeur de base de la propriété <xref:System.Windows.FrameworkElement.Width%2A>, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### À\/Par  
 Si vous définissez les propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> d'une animation, la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> est ignorée.  
  
<a name="otheranimationtypes"></a>   
## Autres types d'animations  
 Les animations From\/To\/By ne sont pas le seul type d'animation fourni par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : il offre également des animations d'image clé et des animations de tracés.  
  
-   Une animation d'image clé est animée avec n'importe quel nombre de valeurs de destination, décrites à l'aide d'images clés.  Pour plus d'informations, consultez [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   Une animation de tracé génère des valeurs de sortie d'un <xref:System.Windows.Media.PathGeometry>.  Pour plus d'informations, consultez [Vue d'ensemble des animations de tracés](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet également de créer vos propres types d'animations personnalisés.  Pour plus d'informations, consultez [Vue d'ensemble des animations personnalisées](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.Timeline>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Vue d'ensemble des animations de tracés](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)   
 [Vue d'ensemble des animations personnalisées](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)   
 [Valeurs cibles d'animation From, To et By, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159988)