---
title: "Conseils et astuces sur les animations | Microsoft Docs"
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
  - "animer des objets (WPF), dépanner"
  - "conseils et astuces sur les animations (WPF)"
  - "animations (WPF), FillBehavior (propriété)"
  - "animations (WPF), utilisation des ressources système"
  - "dépannage des performances (WPF), animation"
  - "conseils et astuces (WPF), animation"
  - "dépannage (WPF), animation"
  - "résoudre les problèmes liés à l'animation (WPF)"
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Conseils et astuces sur les animations
Lorsque vous utilisez des animations dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], de nombreux conseils et astuces peuvent vous permettre d'optimiser vos animations en vous évitant toute frustration.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="generalissuessection"></a>   
## Problèmes généraux  
  
### La position de la barre de défilement ou du curseur se fige après avoir été animée  
 Si vous animez la position d'une barre de défilement ou d'un curseur en utilisant une animation qui a un <xref:System.Windows.Media.Animation.FillBehavior> dont la valeur est<xref:System.Windows.Media.Animation.FillBehavior> \(valeur par défaut\), l'utilisateur ne pourra plus déplacer la barre de défilement ni le curseur.  Cela est dû au fait que, même si l'animation est terminée, elle remplace toujours la valeur de base de la propriété cible.  Pour stopper le remplacement de la valeur actuelle de la propriété, supprimez l'animation ou donnez\-lui un <xref:System.Windows.Media.Animation.FillBehavior> avec une valeur <xref:System.Windows.Media.Animation.FillBehavior>.  Pour obtenir des informations supplémentaires et un exemple, consultez [Définir une propriété après l'avoir animée avec un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### L'animation de la sortie d'une animation n'a aucun effet  
 Vous ne pouvez pas animer un objet qui correspond à la sortie d'une autre animation.  Par exemple, si vous utilisez un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> pour animer le <xref:System.Windows.Shapes.Shape.Fill%2A> d'un <xref:System.Windows.Shapes.Rectangle> à partir d'un <xref:System.Windows.Media.RadialGradientBrush> vers un <xref:System.Windows.Media.SolidColorBrush>, vous ne pouvez animer aucune des propriétés du <xref:System.Windows.Media.RadialGradientBrush> ni du <xref:System.Windows.Media.SolidColorBrush> quelles qu'elles soient.  
  
### Impossible de modifier la valeur d'une propriété après l'avoir animée  
 Dans certains cas, il se peut que vous ne puissiez pas changer la valeur d'une propriété après l'avoir animée, même si l'animation est terminée.  Cela est dû au fait que, même si l'animation est terminée, elle remplace toujours la valeur de base de la propriété.  Pour stopper le remplacement de la valeur actuelle de la propriété, supprimez l'animation ou donnez\-lui un <xref:System.Windows.Media.Animation.FillBehavior> avec une valeur <xref:System.Windows.Media.Animation.FillBehavior>.  Pour obtenir des informations supplémentaires et un exemple, consultez [Définir une propriété après l'avoir animée avec un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### La modification d'une chronologie n'a aucun effet  
 Même si la plupart des propriétés <xref:System.Windows.Media.Animation.Timeline> peuvent être animées et liées aux données, la modification des valeurs de propriété d'un <xref:System.Windows.Media.Animation.Timeline> actif semble n'avoir aucun effet.  Cela est dû au fait que, lorsqu'un <xref:System.Windows.Media.Animation.Timeline> a commencé, le système de minuterie fait une copie du <xref:System.Windows.Media.Animation.Timeline> et l'utilise pour créer un objet <xref:System.Windows.Media.Animation.Clock>.  La modification de l'original n'a aucun effet sur la copie du système.  
  
 Pour qu'un <xref:System.Windows.Media.Animation.Timeline> reflète des modifications, son horloge doit être régénérée et utilisée pour remplacer l'horloge créée précédemment.  Les horloges ne sont pas régénérées automatiquement.  Voici plusieurs façons d'appliquer des modifications de chronologie :  
  
-   Si la chronologie est ou appartient à un <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez alors faire en sorte qu'elle reflète les modifications, en réappliquant sa table de montage séquentiel à l'aide d'un <xref:System.Windows.Media.Animation.BeginStoryboard> ou de la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.  Cela redémarre par contre également l'animation.  Dans le code, vous pouvez utiliser la méthode <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> pour replacer la table de montage séquentiel à sa position précédente.  
  
-   Si vous avez appliqué directement une animation à une propriété à l'aide de la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>, appelez une nouvelle fois la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> et passez\-lui l'animation qui a été modifiée.  
  
-   Si vous travaillez directement au niveau de l'horloge, créez et appliquez un nouveau jeu d'horloges et utilisez\-les pour remplacer le précédent jeu d'horloges générées.  
  
 Pour plus d'informations sur les horloges et les chronologies, consultez [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
### FillBehavior.Stop ne fonctionne pas comme prévu  
 Il arrive parfois que, lorsque vous affectez à la propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> la valeur <xref:System.Windows.Media.Animation.FillBehavior>, cela semble n'avoir aucun effet, par exemple quand une animation est « remise » à une autre car son <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> a la valeur <xref:System.Windows.Media.Animation.HandoffBehavior>.  
  
 L'exemple suivant crée <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> et <xref:System.Windows.Media.TranslateTransform>.  Le <xref:System.Windows.Media.TranslateTransform> sera animé pour déplacer <xref:System.Windows.Shapes.Rectangle> autour de <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 L'exemple dans cette section utilise les objets précédents pour décrire plusieurs cas où la propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> ne se comporte pas de la façon attendue.  
  
#### FillBehavior\="Stop" et HandoffBehavior avec plusieurs animations  
 Vous avez parfois l'impression qu'une animation ignore sa propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> lorsqu'elle est remplacée par une seconde animation.  Prenons l'exemple suivant, dans lequel deux objets <xref:System.Windows.Media.Animation.Storyboard> sont créés et utilisés pour animer le même <xref:System.Windows.Media.TranslateTransform> indiqué dans l'exemple précédent.  
  
 Le premier <xref:System.Windows.Media.Animation.Storyboard>, `B1`, anime la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> de <xref:System.Windows.Media.TranslateTransform> de 0 à 350, ce qui déplace le rectangle de 350 pixels vers la droite.  Lorsque l'animation arrive à la fin de sa durée et s'arrête, la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> revient à sa valeur d'origine, 0.  Par conséquent, le rectangle se déplace de 350 pixels vers la droite, puis revient à sa position d'origine.  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Le second <xref:System.Windows.Media.Animation.Storyboard>, `B2`, anime également la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> du même <xref:System.Windows.Media.TranslateTransform>.  Puisque seule la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> de l'animation dans ce <xref:System.Windows.Media.Animation.Storyboard> est définie, l'animation utilise la valeur actuelle de la propriété qu'elle anime comme valeur de départ.  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Si vous cliquez sur le second bouton alors que le premier <xref:System.Windows.Media.Animation.Storyboard> est en cours de lecture, le comportement suivant est susceptible de se produire :  
  
1.  La première table de montage séquentiel se termine et remet le rectangle à sa position d'origine, car l'animation a un <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> dont la valeur est <xref:System.Windows.Media.Animation.FillBehavior>.  
  
2.  La seconde table de montage séquentiel est appliquée et s'anime à partir de la position actuelle, qui est maintenant de 0, jusqu'à 500.  
  
 **Mais ce n'est pas ce qu'il se passe.** Au lieu de revenir à sa position d'origine, le rectangle continue à se déplacer vers la droite.  Cela est dû au fait que la seconde animation utilise la valeur actuelle de la première animation comme valeur de départ et s'anime à partir de cette valeur jusqu'à 500.  Lorsque la seconde animation remplace la première puisque <xref:System.Windows.Media.Animation.HandoffBehavior> <xref:System.Windows.Media.Animation.HandoffBehavior> est utilisé, le <xref:System.Windows.Media.Animation.FillBehavior> de la première animation n'a pas d'importance.  
  
#### FillBehavior et événement terminé  
 Dans le scénario décrit dans les exemples ci\-après, <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> semble n'avoir aucun effet.  Ici encore, l'exemple utilise un storyboard pour animer la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> de <xref:System.Windows.Media.TranslateTransform> de 0 à 350.  Cependant, cet exemple s'inscrit cette fois à l'événement <xref:System.Windows.Media.Animation.Timeline.Completed>.  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 Le gestionnaire d'événements <xref:System.Windows.Media.Animation.Timeline.Completed> démarre un autre <xref:System.Windows.Media.Animation.Storyboard> qui anime la même propriété à partir de sa valeur actuelle jusqu'à 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Le balisage suivant définit le second <xref:System.Windows.Media.Animation.Storyboard> comme ressource.  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Lorsque vous exécutez le <xref:System.Windows.Media.Animation.Storyboard>, vous vous attendez à ce que la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> de <xref:System.Windows.Media.TranslateTransform> s'anime de 0 à 350, revienne à 0 une fois terminée \(car son paramètre <xref:System.Windows.Media.Animation.FillBehavior> a la valeur <xref:System.Windows.Media.Animation.FillBehavior>\), puis s'anime de 0 à 500.  Au lieu de cela, <xref:System.Windows.Media.TranslateTransform> s'anime de 0 à 350, puis à 500.  
  
 Cela est dû à l'ordre dans lequel [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] déclenche les événements et au fait que les valeurs de propriété sont mises en cache et ne sont pas recalculées sauf si la propriété est invalidée.  L'événement <xref:System.Windows.Media.Animation.Timeline.Completed> est traité en premier car il a été déclenché par la chronologie racine \(le premier <xref:System.Windows.Media.Animation.Storyboard>\).  À ce stade, la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> renvoie toujours sa valeur animée car elle n'a pas encore été invalidée.  Le second <xref:System.Windows.Media.Animation.Storyboard> utilise la valeur mise en cache comme valeur de départ et commence l'animation.  
  
<a name="performancesection"></a>   
## Performances  
  
### Les animations continuent à s'exécuter lorsque vous avez quitté une page  
 Lorsque vous naviguez loin d'une <xref:System.Windows.Controls.Page> qui contient des animations en cours d'exécution, ces dernières continuent à s'exécuter jusqu'à ce que <xref:System.Windows.Controls.Page> soit récupéré par le garbage collector.  Selon le système de navigation utilisé, lorsque vous quittez une page, elle peut rester en mémoire pendant une durée indéfinie, au cours de laquelle ses animations consomment des ressources.  Cela est particulièrement visible lorsqu'une page contient des animations qui s'exécutent constamment \(« ambiantes »\).  
  
 C'est pourquoi il est conseillé d'utiliser l'événement <xref:System.Windows.FrameworkElement.Unloaded> pour supprimer les animations lorsque vous naviguez loin d'une page.  
  
 Il y a différentes manières de supprimer une animation.  Vous pouvez utiliser les techniques suivantes pour supprimer les animations qui appartiennent à un <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Pour supprimer un <xref:System.Windows.Media.Animation.Storyboard> créé avec un déclencheur d'événements, consultez [How to: Remove a Storyboard](http://msdn.microsoft.com/fr-fr/7fe39531-de2f-46a0-a69f-b783d04235ee).  
  
-   Pour utiliser du code afin de supprimer un <xref:System.Windows.Media.Animation.Storyboard>, reportez\-vous à la méthode <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>.  
  
 La technique suivante peut être utilisée quelle que soit la façon dont l'animation a été démarrée.  
  
-   Pour supprimer des animations d'une propriété spécifique, utilisez la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>.  Spécifiez la propriété animée comme premier paramètre et `null` comme second paramètre.  Cela supprime toutes les horloges d'animation de la propriété.  
  
 Pour plus d'informations sur les différentes manières d'animer les propriétés, consultez [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### L'utilisation de Compose HandoffBehavior consomme des ressources système  
 Lorsque vous appliquez un <xref:System.Windows.Media.Animation.Storyboard>, un <xref:System.Windows.Media.Animation.AnimationTimeline> ou un <xref:System.Windows.Media.Animation.AnimationClock> à une propriété à l'aide de <xref:System.Windows.Media.Animation.HandoffBehavior> <xref:System.Windows.Media.Animation.HandoffBehavior>, tous les objets <xref:System.Windows.Media.Animation.Clock> précédemment associés à cette propriété continuent d'utiliser les ressources système ; le système de minuterie ne supprimera pas automatiquement ces horloges.  
  
 Pour éviter tout problème de performances lors de l'application d'un grand nombre d'horloges à l'aide de <xref:System.Windows.Media.Animation.HandoffBehavior>, vous devez supprimer la composition des horloges de la propriété animée une fois leur tâche terminée.  Il existe plusieurs manières de supprimer une horloge.  
  
-   Pour supprimer toutes les horloges d'une propriété, utilisez la méthode <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> ou <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> de l'objet animé.  Spécifiez la propriété animée comme premier paramètre et `null` comme second paramètre.  Cela supprime toutes les horloges d'animation de la propriété.  
  
-   Pour supprimer un <xref:System.Windows.Media.Animation.AnimationClock> spécifique d'une liste d'horloges, utilisez la propriété <xref:System.Windows.Media.Animation.Clock.Controller%2A> de <xref:System.Windows.Media.Animation.AnimationClock> pour récupérer un <xref:System.Windows.Media.Animation.ClockController>, puis appelez la méthode <xref:System.Windows.Media.Animation.ClockController.Remove%2A> de <xref:System.Windows.Media.Animation.ClockController>.  Cela s'effectue généralement dans le gestionnaire d'événements <xref:System.Windows.Media.Animation.Clock.Completed> pour une horloge.  Remarque : seules les horloges racines peuvent être contrôlées par un <xref:System.Windows.Media.Animation.ClockController> ; la propriété <xref:System.Windows.Media.Animation.Clock.Controller%2A> d'une horloge enfant retournera la valeur `null`.  Remarque : l'événement <xref:System.Windows.Media.Animation.Clock.Completed> ne sera pas appelé si la durée effective de l'horloge est illimitée.  Dans un tel cas, l'utilisateur doit déterminer à quel moment appeler l'événement <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Cela constitue principalement un problème pour les animations sur des objets qui ont une durée de vie importante.  Lorsqu'un objet est récupéré par le garbage collector, ses horloges sont également déconnectées et récupérées.  
  
 Pour plus d'informations sur les objets d'horloge, consultez [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)