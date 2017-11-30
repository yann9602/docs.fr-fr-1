---
title: "Vue d’ensemble des Animations From-To-By"
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
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f5eba773a290f1100fcea411919c5c16558e01ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="fromtoby-animations-overview"></a>Vue d'ensemble des animations From/To/By
Cette rubrique explique comment utiliser des animations From/To/By pour animer des propriétés de dépendance. Une animation From/To/By crée une transition entre deux valeurs.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Pour comprendre cette rubrique, vous devez être familiarisé avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalités d’animations. Pour une introduction aux fonctionnalités d’animation, consultez le [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>Qu’est-ce qu’une animation From/To/By ?  
 Un From/To/By animation est un type de <xref:System.Windows.Media.Animation.AnimationTimeline> qui crée une transition entre une valeur de départ et une valeur de fin. La durée pendant laquelle la transition prend fin est déterminée par le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cette animation.  
  
 Vous pouvez appliquer un From/To/By animation à une propriété à l’aide un <xref:System.Windows.Media.Animation.Storyboard> dans le balisage et le code ou à l’aide de la <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode dans le code. Vous pouvez également utiliser une Animation de From/To/By pour créer un <xref:System.Windows.Media.Animation.AnimationClock> et l’appliquer à une ou plusieurs propriétés. Pour plus d’informations sur les différentes façons d’appliquer des animations, consultez la [Vue d’ensemble des techniques d’animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
 Les animations From/To/By ne peuvent pas avoir plus de deux valeurs cibles. Si vous avez besoin d’une animation comportant plus de deux valeurs cibles, utilisez une animation d’image clé. Animations d’image clé sont décrites dans le [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Types d’animation From/To/By  
 Étant donné que les animations génèrent des valeurs de propriété, il existe différents types d’animation pour différents types de propriété. Pour animer une propriété qui prend un <xref:System.Double>, telles que la <xref:System.Windows.FrameworkElement.Width%2A> propriété d’un élément, utilisez une animation qui produit <xref:System.Double> valeurs. Pour animer une propriété qui prend un <xref:System.Windows.Point>, utilisez une animation qui produit <xref:System.Windows.Point> valeurs et ainsi de suite.  
  
 Classes d’animation From/To/By appartiennent à la <xref:System.Windows.Media.Animation> espace de noms et d’utiliser la convention d’affectation de noms suivante :  
  
 *\<Type>* `Animation`  
  
 Où * \<Type >* est le type de valeur que la classe anime.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les classes d’animation From/To/By suivantes.  
  
|Type de propriété|Classe d’animations From/To/By correspondante|  
|-------------------|------------------------------------------------|  
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
## <a name="target-values"></a>Valeurs cibles  
 Une animation From/To/By crée une transition entre deux valeurs cibles. Il est courant de spécifier une valeur de départ (à l’aide la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété) et une valeur de fin (à l’aide du <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété). Toutefois, vous pouvez également spécifier uniquement une valeur de début, une valeur de destination ou une valeur de décalage. Dans ces cas, l’animation obtient la valeur cible manquante de la propriété qui est animée. La liste suivante décrit les différentes manières de spécifier les valeurs cibles d’une animation.  
  
-   **Valeur de départ**  
  
     Utilisez le <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété lorsque vous souhaitez spécifier explicitement la valeur de départ d’une animation. Vous pouvez utiliser la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété, ou avec le <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ou <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété. Si vous spécifiez uniquement le <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété, l’animation passe à partir de cette valeur à la valeur de base de la propriété animée.  
  
-   **Valeur de fin**  
  
     Pour spécifier une valeur de fin d’une animation, utilisez son <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété. Si vous utilisez le <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété par lui-même, l’animation obtient sa valeur de départ à partir de la propriété animée ou de la sortie d’une autre animation appliquée à la même propriété. Vous pouvez utiliser la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété avec le <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété pour spécifier explicitement les valeurs de l’animation.  
  
-   **Valeur de décalage**  
  
     Le <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété vous permet de spécifier un offset au lieu d’un démarrage explicite ou d’une valeur de fin de l’animation. Le <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété d’une animation spécifie de combien l’animation modifie une valeur sur sa durée. Vous pouvez utiliser la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété tout seul ou avec le <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété. Si vous spécifiez uniquement le <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété, l’animation ajoute la valeur de décalage à la valeur de la propriété de base ou à la sortie d’une autre animation.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Utilisation des valeurs From/To/By  
 Les sections suivantes décrivent comment utiliser le <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriétés ensemble ou séparément.  
  
 Les exemples de cette section utilisent chacun une <xref:System.Windows.Media.Animation.DoubleAnimation>, qui est un type d’animation From/To/By, pour animer la <xref:System.Windows.FrameworkElement.Width%2A> propriété d’un <xref:System.Windows.Shapes.Rectangle> qui est 10 pixels indépendants du périphérique haute et 100 pixels indépendants du périphérique larges.  
  
 Bien que chaque exemple utilise un <xref:System.Windows.Media.Animation.DoubleAnimation>, à partir, à et par les propriétés de tous les From/To/By animations se comportent comme des. Bien que chacun de ces exemples utilise un <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez utiliser des animations From/To/By par d’autres moyens. Pour plus d’informations, consultez [Property Animation Techniques Overview](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>De/À  
 Lorsque vous définissez la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> valeurs ensemble, l’animation passe de la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> , valeur à la propriété spécifiée par le <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété.  
  
 L’exemple suivant définit la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété de la <xref:System.Windows.Media.Animation.DoubleAnimation> à 50 et son <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété 300. Par conséquent, le <xref:System.Windows.FrameworkElement.Width%2A> de la <xref:System.Windows.Shapes.Rectangle> est animée de 50 à 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>À  
 Lorsque vous définissez uniquement la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété, l’animation progresse à partir de la valeur de base de la propriété animée ou la sortie d’une animation de composition qui a été précédemment appliquée à la même propriété, à la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété.  
  
 (« Animation de composition » fait référence à un <xref:System.Windows.Media.Animation.ClockState.Active> ou <xref:System.Windows.Media.Animation.ClockState.Filling> animation précédemment appliqué à la même propriété est toujours en vigueur lors de l’animation en cours a été appliquée à l’aide de la <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> comportement de transfert.)  
  
 L’exemple suivant affecte uniquement la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété de la <xref:System.Windows.Media.Animation.DoubleAnimation> à 300. Car aucune valeur de départ a été spécifié, le <xref:System.Windows.Media.Animation.DoubleAnimation> utilise la valeur de base (100) de la <xref:System.Windows.FrameworkElement.Width%2A> propriété comme valeur de départ. Le <xref:System.Windows.FrameworkElement.Width%2A> de la <xref:System.Windows.Shapes.Rectangle> est animée de 100 à la valeur de cible de l’animation de 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Par  
 Lorsque vous définissez uniquement la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété d’une animation, l’animation progresse à partir de la valeur de base de la propriété animée ou la sortie d’une animation de composition à la somme de cette valeur et la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété.  
  
 L’exemple suivant affecte uniquement la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété de la <xref:System.Windows.Media.Animation.DoubleAnimation> à 300. Étant donné que l’exemple ne spécifie pas une valeur de départ, la <xref:System.Windows.Media.Animation.DoubleAnimation> utilise la valeur de base de la <xref:System.Windows.FrameworkElement.Width%2A> propriété, 100, comme valeur de départ. La valeur finale est déterminée en ajoutant la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> valeur de l’animation, 300, à sa valeur de départ, 100:400. Par conséquent, le <xref:System.Windows.FrameworkElement.Width%2A> de la <xref:System.Windows.Shapes.Rectangle> est animée de 100 à 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>From/By  
 Lorsque vous définissez la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> des propriétés d’une animation, l’animation passe de la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> , valeur à la propriété spécifiée par la somme de la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriétés.  
  
 L’exemple suivant définit la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété de la <xref:System.Windows.Media.Animation.DoubleAnimation> à 50 et son <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété 300. La valeur finale est déterminée en ajoutant la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> valeur de l’animation, 300, à sa valeur de départ, 50:350. Par conséquent, le <xref:System.Windows.FrameworkElement.Width%2A> de la <xref:System.Windows.Shapes.Rectangle> est animée de 50 à 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>De  
 Lorsque vous spécifiez uniquement le <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> valeur d’une animation, l’animation passe de la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété, la valeur de base de la propriété animée ou à la sortie d’une animation de composition.  
  
 L’exemple suivant affecte uniquement la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété de la <xref:System.Windows.Media.Animation.DoubleAnimation> à 50. Car aucune valeur de fin a été spécifié, le <xref:System.Windows.Media.Animation.DoubleAnimation> utilise la valeur de base de la <xref:System.Windows.FrameworkElement.Width%2A> propriété, 100, comme valeur finale. Le <xref:System.Windows.FrameworkElement.Width%2A> de la <xref:System.Windows.Shapes.Rectangle> est animée de 50 à la valeur de base de la <xref:System.Windows.FrameworkElement.Width%2A> propriété, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 Si vous définissez à la fois le <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriétés d’une animation, la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété est ignorée.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Autres types d’animations  
 Animations From/To/By ne sont pas le seul type d’animations qui [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit : il fournit également des animations d’image clé et les animations de chemin d’accès.  
  
-   Une animation d’image clé est animée avec n’importe quel nombre de valeurs de destination et décrite à l’aide d’images clés. Pour plus d’informations, consultez la [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   Une animation de tracé génère des valeurs de sortie à partir d’un <xref:System.Windows.Media.PathGeometry>. Pour plus d’informations, consultez la [vue d’ensemble des Animations de chemin d’accès](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet également de créer vos propres types d’animations personnalisées. Pour plus d’informations, consultez la [vue d’ensemble des Animations personnalisés](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d'ensemble des plans conceptuels](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Vue d'ensemble des animations de tracés](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [Vue d'ensemble des animations personnalisées](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)  
 [Exemple de valeurs cibles d’animation From, To et By](http://go.microsoft.com/fwlink/?LinkID=159988)
