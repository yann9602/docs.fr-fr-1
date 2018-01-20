---
title: Conseils et astuces sur les animations
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
- troubleshooting [WPF], animation
- animations [WPF], FillBehavior property
- troubleshooting animation [WPF]
- animating objects [WPF], troubleshooting
- animation tips and tricks [WPF]
- tips and tricks [WPF], animation
- performance troubleshooting [WPF], animation
- animations [WPF], use of system resources
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 210f8ff8840f579d352cc579f80f38488b998c5a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="animation-tips-and-tricks"></a>Conseils et astuces sur les animations
Lorsque vous utilisez des animations dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], il existe de nombreux conseils et astuces qui peuvent rendre vos animations plus performantes et vous permettre d’économiser frustration.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Problèmes généraux  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>L’animation de la position d’une barre de défilement ou d’un curseur bloque cet élément  
 Si vous animez la position d’une barre de défilement ou le curseur à l’aide d’une animation qui a un <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (la valeur par défaut), l’utilisateur seront plus en mesure de déplacer la barre de défilement ni le curseur. Cela survient car l’animation, même si elle est terminée, remplace toujours la valeur de base de la propriété cible. Pour arrêter l’animation à partir de la substitution de la valeur de propriété actuelle, supprimez-le, ou pour lui donner un <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Pour plus d’informations et obtenir un exemple, consultez [définir une propriété après l’animation avec une table de montage séquentiel](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>L’animation de la sortie d’une animation n’a aucun effet  
 Vous ne pouvez pas animer un objet qui est le résultat d’une autre animation. Par exemple, si vous utilisez un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> pour animer la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle> à partir d’un <xref:System.Windows.Media.RadialGradientBrush> à un <xref:System.Windows.Media.SolidColorBrush>, Impossible d’animer les propriétés de la <xref:System.Windows.Media.RadialGradientBrush> ou <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Impossible de modifier la valeur d’une propriété après l’avoir animée  
 Dans certains cas, il peut sembler que vous ne pouvez pas modifier la valeur d’une propriété une fois qu’elle a été animée, même une fois l’animation terminée. Cela survient car l’animation, même si elle est terminée, remplace toujours la valeur de base de la propriété. Pour arrêter l’animation à partir de la substitution de la valeur de propriété actuelle, supprimez-le, ou pour lui donner un <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Pour plus d’informations et obtenir un exemple, consultez [définir une propriété après l’animation avec une table de montage séquentiel](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>La modification d’une chronologie n’a aucun effet  
 Bien que la plupart des <xref:System.Windows.Media.Animation.Timeline> propriétés peuvent être animées et peuvent être lié aux données, la modification des valeurs de propriété d’un actif <xref:System.Windows.Media.Animation.Timeline> semble n’avoir aucun effet. C’est parce que, quand un <xref:System.Windows.Media.Animation.Timeline> est commencé, le système de minuterie fait une copie de la <xref:System.Windows.Media.Animation.Timeline> et l’utilise pour créer un <xref:System.Windows.Media.Animation.Clock> objet. La modification de l’original n’a aucun effet sur la copie du système.  
  
 Pour un <xref:System.Windows.Media.Animation.Timeline> pour refléter les modifications, son horloge doit être régénérée et utilisée pour remplacer l’horloge créée précédemment. Les horloges ne sont pas régénérées automatiquement pour vous. Voici plusieurs façons d’appliquer des modifications de chronologie :  
  
-   Si la chronologie est ou appartient à un <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez rendre reflète les modifications en réappliquant sa table de montage séquentiel à l’aide un <xref:System.Windows.Media.Animation.BeginStoryboard> ou <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> (méthode). Cela a pour effet secondaire de redémarrer également l’animation. Dans le code, vous pouvez utiliser la <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> méthode pour faire avancer le plan conceptuel vers à sa position précédente.  
  
-   Si vous avez appliqué une animation directement à une propriété à l’aide de la <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode, appelez la <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode et passez-lui l’animation qui a été modifiée.  
  
-   Si vous travaillez directement au niveau de l’horloge, créez et appliquez un nouveau jeu d’horloges et utilisez-le pour remplacer le précédent jeu d’horloges généré.  
  
 Pour plus d’informations et les chronologies, consultez [Animation et vue d’ensemble du système de minuterie](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop ne fonctionne pas comme prévu  
 Il se peut que lors de la définition la <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété <xref:System.Windows.Media.Animation.FillBehavior.Stop> semble n’avoir aucun effet, par exemple quand une animation « transmet » à l’autre, car il a un <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> définition de <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Canvas>, un <xref:System.Windows.Shapes.Rectangle> et un <xref:System.Windows.Media.TranslateTransform>. Le <xref:System.Windows.Media.TranslateTransform> sera animé pour déplacer le <xref:System.Windows.Shapes.Rectangle> autour de le <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Les exemples de cette section utilisent les objets précédents pour décrire plusieurs cas où le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété ne se comporte pas comme vous pourriez vous attendre à.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" et HandoffBehavior avec plusieurs animations  
 Parfois, il semble qu’une animation ignore sa <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété lorsqu’elle est remplacée par une seconde animation. Prenons l’exemple suivant, qui crée deux <xref:System.Windows.Media.Animation.Storyboard> d’objets et les utilise pour animer la même <xref:System.Windows.Media.TranslateTransform> indiqué dans l’exemple précédent.  
  
 La première <xref:System.Windows.Media.Animation.Storyboard>, `B1`, anime la <xref:System.Windows.Media.TranslateTransform.X%2A> propriété de la <xref:System.Windows.Media.TranslateTransform> de 0 à 350, ce qui déplace le rectangle de 350 pixels vers la droite. Lorsque l’animation atteint la fin de sa durée et s’arrête, le <xref:System.Windows.Media.TranslateTransform.X%2A> propriété revient à sa valeur d’origine, 0. Par conséquent, le rectangle se déplace vers la droite de 350 pixels puis revient à sa position d’origine.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 La seconde <xref:System.Windows.Media.Animation.Storyboard>, `B2`, anime également la <xref:System.Windows.Media.TranslateTransform.X%2A> propriété du même <xref:System.Windows.Media.TranslateTransform>. Étant donné qu’uniquement le <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété de l’animation dans ce <xref:System.Windows.Media.Animation.Storyboard> est défini, l’animation utilise la valeur actuelle de la propriété qu’elle anime comme valeur de départ.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Si vous cliquez sur le deuxième bouton lors de la première <xref:System.Windows.Media.Animation.Storyboard> est actif, vous pouvez vous attendre le comportement suivant :  
  
1.  La première table de montage séquentiel se termine et renvoie le rectangle à sa position d’origine, car l’animation a un <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2.  Le deuxième storyboard est appliqué et s’anime à partir de la position actuelle, qui est désormais 0, jusqu'à 500.  
  
 **Mais ce n’est pas ce qui se produit.** Au lieu de cela, le rectangle ne revient pas. Il continue à se déplacer vers la droite. Cela se produit car la deuxième animation utilise la valeur actuelle de la première animation comme valeur de départ, et anime à partir de cette valeur à 500. Lorsque la seconde animation remplace la première, car le <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> est utilisé, le <xref:System.Windows.Media.Animation.FillBehavior> de la première animation n’a pas d’importance.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior et l’événement terminé  
 Les exemples suivants montrent un autre scénario dans lequel le <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> semble n’avoir aucun effet. Là encore, l’exemple utilise une table de montage séquentiel pour animer la <xref:System.Windows.Media.TranslateTransform.X%2A> propriété de la <xref:System.Windows.Media.TranslateTransform> de 0 à 350. Toutefois, cette fois l’exemple inscrit pour le <xref:System.Windows.Media.Animation.Timeline.Completed> événement.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 Le <xref:System.Windows.Media.Animation.Timeline.Completed> Gestionnaire d’événements démarre un autre <xref:System.Windows.Media.Animation.Storyboard> qui anime la même propriété à partir de sa valeur actuelle à 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Voici le balisage qui définit le deuxième <xref:System.Windows.Media.Animation.Storyboard> en tant que ressource.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Lorsque vous exécutez le <xref:System.Windows.Media.Animation.Storyboard>, vous pourriez vous attendre le <xref:System.Windows.Media.TranslateTransform.X%2A> propriété de la <xref:System.Windows.Media.TranslateTransform> pour animer de 0 à 350, puis revenez à 0 après avoir terminé (parce qu’elle a un <xref:System.Windows.Media.Animation.FillBehavior> définition de <xref:System.Windows.Media.Animation.FillBehavior.Stop>), puis s’anime de 0 à 500. Au lieu de cela, le <xref:System.Windows.Media.TranslateTransform> réalise une animation à partir de 0 à 350, puis à 500.  
  
 Cela est dû à l’ordre dans lequel [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] déclenche des événements et les valeurs de propriété sont mises en cache et ne sont pas recalculées sauf si la propriété est invalidée. Le <xref:System.Windows.Media.Animation.Timeline.Completed> événement est traité en premier, car il a été déclenché par la chronologie racine (le premier <xref:System.Windows.Media.Animation.Storyboard>). À ce stade, le <xref:System.Windows.Media.TranslateTransform.X%2A> propriété retourne toujours sa valeur animée car elle n’a pas encore été invalidée. La seconde <xref:System.Windows.Media.Animation.Storyboard> utilise la valeur mise en cache comme valeur de départ et commence l’animation.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Performances  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Les animations continuent à s’exécuter après avoir quitté une page  
 Lorsque vous accédez à un <xref:System.Windows.Controls.Page> qui contient les animations en cours d’exécution, ces dernières continuent d’être lu tant que le <xref:System.Windows.Controls.Page> est le garbage collecté. Selon le système de navigation vous utilisez, une page que vous quittez peut rester en mémoire pendant une durée indéterminée tout en consommant des ressources avec ses animations. Cela est particulièrement visible lorsqu’une page contient des animations en exécution constante (« ambiantes »).  
  
 Pour cette raison, il est judicieux d’utiliser le <xref:System.Windows.FrameworkElement.Unloaded> événement à supprimer les animations lorsque vous quittez une page.  
  
 Il existe différentes manières de supprimer une animation. Les techniques suivantes peuvent être utilisées pour supprimer les animations qui appartiennent à un <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Pour supprimer un <xref:System.Windows.Media.Animation.Storyboard> vous avez commencé avec un déclencheur d’événements, consultez [Comment : supprimer un Storyboard](http://msdn.microsoft.com/library/7fe39531-de2f-46a0-a69f-b783d04235ee).  
  
-   Pour utiliser le code pour supprimer un <xref:System.Windows.Media.Animation.Storyboard>, consultez le <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> (méthode).  
  
 La technique suivante peut être utilisée, quelle que soit la façon dont l’animation a été démarrée.  
  
-   Pour supprimer des animations d’une propriété spécifique, utilisez le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> (méthode). Spécifiez la propriété animée comme premier paramètre, et `null` comme deuxième. Cela supprimera toutes les horloges d’animation de la propriété.  
  
 Pour plus d’informations sur les différentes façons pour animer des propriétés, consultez [Property Animation Techniques Overview](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>L’utilisation de la composition HandoffBehavior consomme des ressources système  
 Lorsque vous appliquez un <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>, ou <xref:System.Windows.Media.Animation.AnimationClock> à une propriété à l’aide de la <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>, tout <xref:System.Windows.Media.Animation.Clock> objets précédemment associés à cette propriété continuent de consommer des ressources système ; le système de minuterie n’est pas Supprimez ces horloges automatiquement.  
  
 Pour éviter les problèmes de performances lorsque vous appliquez un grand nombre d’horloges à l’aide de <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, vous devez supprimer la composition des horloges de la propriété animée lorsqu’ils ont terminé. Il existe plusieurs manières de supprimer une horloge.  
  
-   Pour supprimer toutes les horloges d’une propriété, utilisez la <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> ou <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> méthode de l’objet animé. Spécifiez la propriété animée comme premier paramètre, et `null` comme deuxième. Cela supprimera toutes les horloges d’animation de la propriété.  
  
-   Pour supprimer un spécifique <xref:System.Windows.Media.Animation.AnimationClock> à partir d’une liste d’horloges, utilisez la <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriété de la <xref:System.Windows.Media.Animation.AnimationClock> pour récupérer un <xref:System.Windows.Media.Animation.ClockController>, puis appelez le <xref:System.Windows.Media.Animation.ClockController.Remove%2A> méthode de la <xref:System.Windows.Media.Animation.ClockController>. Cette opération s’effectue généralement le <xref:System.Windows.Media.Animation.Clock.Completed> Gestionnaire d’événements pour une horloge. Notez que seules les horloges racine peuvent être contrôlées par un <xref:System.Windows.Media.Animation.ClockController>; le <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriété d’une horloge enfant retourne `null`. Notez également que le <xref:System.Windows.Media.Animation.Clock.Completed> événement ne sera pas appelé si la durée effective de l’horloge est illimitée.  Dans ce cas, l’utilisateur devra déterminer à quel moment appeler <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Il s’agit principalement d’un problème pour les animations sur des objets qui ont une durée de vie longue.  Lorsqu’un objet est récupéré par le garbage collector, ses horloges sont également déconnectées et récupérées.  
  
 Pour plus d’informations sur les objets clock, consultez [Animation et vue d’ensemble du système de minuterie](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
