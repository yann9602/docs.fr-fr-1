---
title: "Vue d&#39;ensemble des techniques d&#39;animation de propri&#233;t&#233;s | Microsoft Docs"
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
  - "animation, propriétés, méthodes pour"
  - "propriétés, méthodes pour animer"
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble des techniques d&#39;animation de propri&#233;t&#233;s
Cette rubrique décrit les différentes approches en matière des propriétés d'animation : tables de montage séquentiel, animations locales, horloges et animations image par image.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## Composants requis  
 Pour comprendre cette rubrique, vous devez être familiarisé avec les fonctionnalités des animations de base décrites dans la [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="summary"></a>   
## Différentes façons d'animer  
 Dans la mesure où il existe différent scénarios d'animer les propriétés, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit plusieurs approches pour l'animation des propriétés.  
  
 Pour chaque approche, le tableau suivant indique si elle peut être utilisée par instance, dans les styles, les modèles des contrôles ou dans les modèles des données ; si elle peut être utilisée en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; et si l'approche vous permet de contrôler l'animation de manière interactive.  « Par instance » fait référence à la technique d'application d'une animation ou d'un storyboard directement aux instances d'un objet, plutôt que dans un style, un modèle de contrôle ou un modèle de données.  
  
|Technique d'animation|Scénarios|Prend en charge XAML|Pilotable de manière interactive|  
|---------------------------|---------------|--------------------------|--------------------------------------|  
|Animation de la table de montage séquentiel|Par instance, <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.DataTemplate>|Oui|Oui|  
|Animation locale|Par instance|Non|Non|  
|Animation horloge|Par instance|Non|Oui|  
|Animation image par image|Par instance|Non|N\/A|  
  
<a name="storyboard_animations"></a>   
## Animations de la table de montage séquentiel  
 Utilisez un <xref:System.Windows.Media.Animation.Storyboard> quand vous voulez définir et appliquer vos animations en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], contrôler de manière interactive vos animations après leur démarrage, créer une arborescence complexe d'animations ou effectuer une animation dans <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> ou <xref:System.Windows.DataTemplate>.  Pour animer un objet par le biais d'un <xref:System.Windows.Media.Animation.Storyboard>, il doit s'agir d'un <xref:System.Windows.FrameworkElement> ou d'un <xref:System.Windows.FrameworkContentElement>, ou il doit être utilisé pour définir un <xref:System.Windows.FrameworkElement> ou un <xref:System.Windows.FrameworkContentElement>.  Pour plus d'informations, consultez la [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> est un conteneur de type spécial <xref:System.Windows.Media.Animation.Timeline> qui fournit des informations de ciblage pour les animations qu'il contient.  Pour animer avec un <xref:System.Windows.Media.Animation.Storyboard>, vous devez effectuer les trois étapes suivantes.  
  
1.  Déclarez un <xref:System.Windows.Media.Animation.Storyboard> et une ou plusieurs animations.  
  
2.  Utilisez les [propriétés attachées](GTMT)<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> pour spécifier l'objet cible et la propriété de chaque animation.  
  
3.  \(Code uniquement\) Définissez un <xref:System.Windows.NameScope> pour un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.  Inscrivez les noms des objets à animer avec <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.  
  
4.  Lancez le <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Le lancement de <xref:System.Windows.Media.Animation.Storyboard> applique des animations aux propriétés qu'elles animent et les démarre.  Il existe deux façon de lancer un <xref:System.Windows.Media.Animation.Storyboard> : vous pouvez utiliser la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> fournie par la classe <xref:System.Windows.Media.Animation.Storyboard>, ou vous pouvez utiliser une action <xref:System.Windows.Media.Animation.BeginStoryboard>.  La seule façon d'effectuer une animation dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] consiste à utiliser une action <xref:System.Windows.Media.Animation.BeginStoryboard>. Une action <xref:System.Windows.Media.Animation.BeginStoryboard> peut être utilisée dans un <xref:System.Windows.EventTrigger>, une propriété <xref:System.Windows.Trigger> ou un <xref:System.Windows.DataTrigger>.  
  
 Le tableau suivant indique les différents endroits où chaque technique de démarrage de <xref:System.Windows.Media.Animation.Storyboard> est prise en charge : par instance, style, modèle de contrôle et modèle de données.  
  
|La table de montage séquentiel commence à être utilisée…|Par instance|Style|Modèle de contrôle|Modèle de données|Exemple|  
|--------------------------------------------------------------|------------------|-----------|------------------------|-----------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> et un <xref:System.Windows.EventTrigger>|Oui|Oui|Oui|Oui|[Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> et une propriété <xref:System.Windows.Trigger>|Non|Oui|Oui|Oui|[Déclencher une animation en cas de modification d'une valeur de propriété](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> et un <xref:System.Windows.DataTrigger>|Non|Oui|Oui|Oui|[How to: Trigger an Animation When Data Changes](http://msdn.microsoft.com/fr-fr/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|Méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Oui|Non|Non|Non|[Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Pour plus d'informations sur les objets <xref:System.Windows.Media.Animation.Storyboard>, consultez [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
## Animations locales  
 Les animations locales offrent un moyen pratique pour animer une [propriété de dépendance](GTMT) de n'importe quel objet <xref:System.Windows.Media.Animation.Animatable>.  Utilisez les animations locales lorsque vous voulez appliquer une animation unique à une propriété et que vous n'avez pas besoin de contrôler l'animation de manière interactive une fois qu'elle a démarré.  À la différence d'une animation <xref:System.Windows.Media.Animation.Storyboard>, une animation locale peut animer un objet qui n'est pas associé à un <xref:System.Windows.FrameworkElement> ou un <xref:System.Windows.FrameworkContentElement>.  Vous n'avez pas non à définir un <xref:System.Windows.NameScope> pour ce type d'animation.  
  
 Les animations locales peuvent uniquement être utilisées dans le code, et ne peuvent pas être définies dans les styles, les modèles de contrôle ou les modèles de données.  Une animation locale ne peut pas être contrôlée de manière interactive une fois qu'elle a démarré.  
  
 Pour effectuer une animation à l'aide d'une animation locale, exécutez les étapes suivantes.  
  
1.  Créez un objet <xref:System.Windows.Media.Animation.AnimationTimeline>.  
  
2.  Utilisez la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> de l'objet que vous voulez animer pour appliquer le <xref:System.Windows.Media.Animation.AnimationTimeline> à la propriété que vous spécifiez.  
  
 L'exemple suivant montre comment animer la largeur et la couleur d'arrière\-plan d'un <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## Animations Clock  
 Utilisez des objets <xref:System.Windows.Media.MediaPlayer.Clock%2A> lorsque vous voulez animer sans utiliser un <xref:System.Windows.Media.Animation.Storyboard> et que vous voulez créer des arborescences de minutage complexes ou contrôler interactivement des animations après leur démarrage.  Vous pouvez utiliser des objets Clock pour animer une [propriété de dépendance](GTMT) de n'importe quel objet <xref:System.Windows.Media.Animation.Animatable>.  
  
 Vous ne pouvez pas utiliser des objets <xref:System.Windows.Media.Animation.Clock> directement pour effectuer des animations dans les styles, les modèles de contrôle ou les modèles de données.  \(Le système d'animation et de minutage utilise en fait des objets <xref:System.Windows.Media.Animation.Clock> pour effectuer des animations dans les styles, les modèles de contrôle et les modèles de données, mais il doit créer les objets <xref:System.Windows.Media.Animation.Clock> pour vous à partir d'un <xref:System.Windows.Media.Animation.Storyboard>.  Pour plus d'informations sur les relations entre les objets <xref:System.Windows.Media.Animation.Storyboard> et les objets <xref:System.Windows.Media.Animation.Clock>, consultez [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).\)  
  
 Pour appliquer un <xref:System.Windows.Media.Animation.Clock> unique à une propriété, exécutez les étapes suivantes.  
  
1.  Créez un objet <xref:System.Windows.Media.Animation.AnimationTimeline>.  
  
2.  Utilisez la méthode <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> de <xref:System.Windows.Media.Animation.AnimationTimeline> pour créer un <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3.  Utilisez la méthode <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> de l'objet que vous voulez animer pour appliquer le <xref:System.Windows.Media.Animation.AnimationClock> à la propriété que vous spécifiez.  
  
 L'exemple suivant montre comment créer un <xref:System.Windows.Media.Animation.AnimationClock> et l'appliquer à deux propriétés similaires.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Pour créer une arborescence et l'utiliser afin d'animer des propriétés, exécutez les étapes suivantes.  
  
1.  Utilisez les objets <xref:System.Windows.Media.Animation.ParallelTimeline> et <xref:System.Windows.Media.Animation.AnimationTimeline> pour créer l'arborescence de minutage.  
  
2.  Utilisez <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> de la racine <xref:System.Windows.Media.Animation.ParallelTimeline> pour créer un <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3.  Itérez au sein de <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> de <xref:System.Windows.Media.Animation.ClockGroup> et appliquez ses objets enfants <xref:System.Windows.Media.Animation.Clock>.  Pour chaque enfant <xref:System.Windows.Media.Animation.AnimationClock>, utilisez la méthode <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> de l'objet que vous voulez animer pour appliquer le <xref:System.Windows.Media.Animation.AnimationClock> à la propriété que vous spécifiez.  
  
 Pour plus d'informations sur les objets Clock, consultez [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## Animation image par image : ignorer le système d'animation et de minutage  
 Utilisez cette approche si vous devez ignorer entièrement le système d'animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Cette approche est utilisée pour les scénarios d'animations physiques dans lesquels chaque étape de l'animation nécessite que les objets animés soient recalculés en fonction du dernier jeu d'interactions d'objets.  
  
 Les animations image par image ne peuvent pas être définies dans les styles, les modèles de contrôle ou les modèles de données.  
  
 Pour effectuer une animation image par image, vous vous inscrivez à l'événement <xref:System.Windows.Media.CompositionTarget.Rendering> de l'objet qui contient les objets à animer.  Cette méthode du gestionnaire d'événements est appelée une fois par trame.  À chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l'[arborescence visuelle](GTMT) sur l'arborescence de composition, la méthode du gestionnaire d'événements est appelée.  
  
 Dans le gestionnaire d'événements, effectuez les calculs nécessaires à l'effet de votre animation et définissez les propriétés des objets à animer avec ces valeurs.  
  
 Pour obtenir l'heure de la présentation de l'image actuelle, le <xref:System.EventArgs> associé à cet événement peut être casté en <xref:System.Windows.Media.RenderingEventArgs>, qui fournit une propriété <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> pouvant être utilisée pour obtenir l'heure de rendu de l'image actuelle.  
  
 Pour plus d'informations, consultez la page <xref:System.Windows.Media.CompositionTarget.Rendering>.  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)