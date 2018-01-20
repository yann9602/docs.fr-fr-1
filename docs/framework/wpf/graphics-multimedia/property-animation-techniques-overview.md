---
title: "Vue d'ensemble des techniques d'animation de propriétés"
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
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ba7c580963214cdfede605f086b6b6c7ecb5657
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="property-animation-techniques-overview"></a>Vue d'ensemble des techniques d'animation de propriétés
Cette rubrique décrit les différentes approches pour animer des propriétés : tables de montage séquentiel, animations locales, horloges et animations par image.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Pour comprendre cette rubrique, vous devez connaître les fonctionnalités de base utilisées pour l’animation, décrites dans [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="summary"></a>   
## <a name="different-ways-to-animate"></a>Différentes méthodes d’animation  
 Puisque de nombreux scénarios différents d’animation de propriétés existent, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propose plusieurs approches pour animer des propriétés.  
  
 Pour chaque approche, le tableau suivant indique si elle peut être utilisée par instance, dans des styles, dans des modèles de contrôle ou dans des modèles de données ; si elle peut être utilisée en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; et si l’approche vous permet de contrôler l’animation de manière interactive.  « Par instance » fait référence à la technique consistant à appliquer une animation ou une table de montage séquentiel directement aux instances d’un objet, plutôt qu’à un style, un modèle de contrôle ou un modèle de données.  
  
|Technique d’animation|Scénarios|XAML pris en charge|Contrôlable de manière interactive|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animation de table de montage séquentiel|Per-instance, <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.DataTemplate>|Oui|Oui|  
|Animation locale|Par instance|Non|Non|  
|Animation horloge|Par instance|Non|Oui|  
|Animation par image|Par instance|Non|N/A|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>Animations de table de montage séquentiel  
 Utilisez un <xref:System.Windows.Media.Animation.Storyboard> lorsque vous souhaitez définir et appliquer des animations dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]de manière interactive contrôler vos animations après leur démarrent, créer une arborescence complexe d’animations ou animer dans un <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> ou <xref:System.Windows.DataTemplate>. Pour un objet à animer par un <xref:System.Windows.Media.Animation.Storyboard>, il doit être un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, ou il doit être utilisé pour définir un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Pour plus d’informations, consultez l’article [Vue d’ensemble des tables de montage séquentiel](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> est un type spécial de conteneur <xref:System.Windows.Media.Animation.Timeline> qui fournit des informations de ciblage pour les animations qu’il contient. Pour animer avec un <xref:System.Windows.Media.Animation.Storyboard>, vous effectuez les trois étapes suivantes.  
  
1.  Déclarez un <xref:System.Windows.Media.Animation.Storyboard> et un ou plusieurs des animations.  
  
2.  Utilisez le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> jointes propriétés pour spécifier l’objet cible et la propriété de chaque animation.  
  
3.  (Code uniquement) Définir un <xref:System.Windows.NameScope> pour un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Inscrire les noms des objets à animer avec <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.  
  
4.  Commencer le <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Depuis un <xref:System.Windows.Media.Animation.Storyboard> applique des animations aux propriétés qu’ils animent et les démarre. Il existe deux façons pour commencer un <xref:System.Windows.Media.Animation.Storyboard>: vous pouvez utiliser la <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> méthode fournie par le <xref:System.Windows.Media.Animation.Storyboard> classe, ou vous pouvez utiliser un <xref:System.Windows.Media.Animation.BeginStoryboard> action. La seule façon pour animer dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] consiste à utiliser un <xref:System.Windows.Media.Animation.BeginStoryboard> action. A <xref:System.Windows.Media.Animation.BeginStoryboard> action peut être utilisée dans un <xref:System.Windows.EventTrigger>, propriété <xref:System.Windows.Trigger>, ou un <xref:System.Windows.DataTrigger>.  
  
 Le tableau suivant présente les différents emplacements où chaque <xref:System.Windows.Media.Animation.Storyboard> commencer technique est pris en charge : par instance, le style, le modèle de contrôle et le modèle de données.  
  
|La table de montage séquentiel démarre à l’aide de…|Par instance|Style|Modèle de contrôle|Modèle de données|Exemple|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>et un<xref:System.Windows.EventTrigger>|Oui|Oui|Oui|Oui|[Animer une propriété à l’aide d’une table de montage séquentiel](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>et une propriété<xref:System.Windows.Trigger>|Non|Oui|Oui|Oui|[Déclencher une animation en cas de modification d’une valeur de propriété](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>et un<xref:System.Windows.DataTrigger>|Non|Oui|Oui|Oui|[Comment : déclencher une animation en cas de modification de données](http://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|Méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Oui|Non|Non|Non|[Animer une propriété à l’aide d’une table de montage séquentiel](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Pour plus d’informations sur <xref:System.Windows.Media.Animation.Storyboard> , consultez la [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
## <a name="local-animations"></a>Animations locales  
 Animations locales offrent un moyen pratique pour animer une propriété de dépendance de n’importe quel <xref:System.Windows.Media.Animation.Animatable> objet. Utilisez les animations locales lorsque vous souhaitez appliquer une seule animation à une propriété et quand vous n’avez pas besoin de contrôler de manière interactive l’animation après son démarrage. Contrairement à un <xref:System.Windows.Media.Animation.Storyboard> animation, une animation locale peut animer un objet qui n’est pas associé à un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Vous ne devez également définir un <xref:System.Windows.NameScope> pour ce type d’animation.  
  
 Les animations locales peuvent uniquement être utilisées dans le code et ne peuvent pas être définies dans des styles, modèles de contrôle ou modèles de données. Une animation locale ne peut pas être contrôlée de façon interactive après son démarrage.  
  
 Pour animer à l’aide d’une animation locale, procédez comme suit.  
  
1.  Créer un <xref:System.Windows.Media.Animation.AnimationTimeline> objet.  
  
2.  Utilisez le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode de l’objet que vous souhaitez animer pour appliquer le <xref:System.Windows.Media.Animation.AnimationTimeline> à la propriété que vous spécifiez.  
  
 L’exemple suivant montre comment animer la couleur d’arrière-plan et de largeur d’un <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Animation horloge  
 Utilisez <xref:System.Windows.Media.MediaPlayer.Clock%2A> objets lorsque vous souhaitez animer sans utiliser un <xref:System.Windows.Media.Animation.Storyboard> et vous souhaitez créer des arborescences de minutage complexes ou contrôler interactivement des animations après leur démarrage. Vous pouvez utiliser des objets Clock pour animer une propriété de dépendance de n’importe quel <xref:System.Windows.Media.Animation.Animatable> objet.  
  
 Vous ne pouvez pas utiliser <xref:System.Windows.Media.Animation.Clock> objets directement à animer dans les styles, modèles de contrôle ou les modèles de données. (Le système d’animation et le minutage utilise en fait <xref:System.Windows.Media.Animation.Clock> objets à animer dans les styles, les modèles de contrôle et les modèles de données, mais il doivent créer ces derniers <xref:System.Windows.Media.Animation.Clock> objets pour vous un <xref:System.Windows.Media.Animation.Storyboard>. Pour plus d’informations sur la relation entre <xref:System.Windows.Media.Animation.Storyboard> objets et <xref:System.Windows.Media.Animation.Clock> , consultez la [Animation et vue d’ensemble du système de minuterie](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).)  
  
 Pour appliquer une seule <xref:System.Windows.Media.Animation.Clock> à une propriété, vous effectuez les étapes suivantes.  
  
1.  Créer un <xref:System.Windows.Media.Animation.AnimationTimeline> objet.  
  
2.  Utilisez le <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> méthode de la <xref:System.Windows.Media.Animation.AnimationTimeline> pour créer un <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3.  Utilisez le <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> méthode de l’objet que vous souhaitez animer pour appliquer le <xref:System.Windows.Media.Animation.AnimationClock> à la propriété que vous spécifiez.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Media.Animation.AnimationClock> et l’appliquer à deux propriétés similaires.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Pour créer une arborescence de minutage et l’utiliser pour animer des propriétés, effectuez les étapes suivantes.  
  
1.  Utilisez <xref:System.Windows.Media.Animation.ParallelTimeline> et <xref:System.Windows.Media.Animation.AnimationTimeline> objets pour créer l’arborescence de minutage.  
  
2.  Utilisez le <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> de la racine de <xref:System.Windows.Media.Animation.ParallelTimeline> pour créer un <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3.  Itérer au sein du <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> de la <xref:System.Windows.Media.Animation.ClockGroup> et appliquer ses enfants <xref:System.Windows.Media.Animation.Clock> objets. Pour chaque <xref:System.Windows.Media.Animation.AnimationClock> enfant, utilisez la <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> méthode de l’objet que vous souhaitez animer pour appliquer le <xref:System.Windows.Media.Animation.AnimationClock> à la propriété que vous spécifiez.  
  
 Pour plus d’informations sur les objets Clock, consultez [Vue d’ensemble de l’animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Animation par image : ignorer le système d’animation et de minutage  
 Utilisez cette approche lorsque vous devez ignorer entièrement le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Un scénario pour cette approche est l’animation physique, où pour chaque étape de l’animation les objets doivent être traités une nouvelle fois en fonction du dernier jeu d’interactions d’objet.  
  
 Les animations par image ne peuvent pas être définies dans des styles, modèles de contrôle ou modèles de données.  
  
 Pour animer frame par frame, vous inscrivez pour le <xref:System.Windows.Media.CompositionTarget.Rendering> événement de l’objet qui contient les objets à animer. Cette méthode de gestionnaire d’événements est appelée une fois par image. Chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l’arborescence visuelle sur l’arborescence de composition, votre méthode de gestionnaire d’événements est appelée.  
  
 Dans votre gestionnaire d’événements, effectuez les calculs nécessaires pour votre effet d’animation et définissez les propriétés des objets à animer avec ces valeurs.  
  
 Pour obtenir l’heure de présentation pour le frame actuel, le <xref:System.EventArgs> associé à cet événement peut être casté en <xref:System.Windows.Media.RenderingEventArgs>, qui fournissent un <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> heure de rendu de propriété que vous pouvez utiliser pour obtenir le frame actuel.  
  
 Pour plus d’informations, consultez le <xref:System.Windows.Media.CompositionTarget.Rendering> page.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d'ensemble des plans conceptuels](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
