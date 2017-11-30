---
title: Vue d'ensemble des comportements de minutage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ac6671033a439051b062ddae70649a63bacd4979
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="timing-behaviors-overview"></a>Vue d'ensemble des comportements de minutage
Cette rubrique décrit les comportements de minutage d’animations et d’autres <xref:System.Windows.Media.Animation.Timeline> objets.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Pour comprendre cette rubrique, vous devez connaître les fonctionnalités de base utilisées pour l’animation. Pour plus d’informations, consultez la [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Types de chronologie  
 A <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps. Elle fournit des propriétés qui vous permettent de spécifier la longueur de ce segment, le moment où il doit démarrer, combien de fois il doit se répéter, à quelle vitesse le temps s’écoule dans ce segment et bien plus encore.  
  
 Les classes qui héritent de la classe de chronologie fournissent des fonctionnalités supplémentaires, comme la lecture de médias et d’animations. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit les éléments suivants <xref:System.Windows.Media.Animation.Timeline> types.  
  
|Type de chronologie|Description|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|De classe de base abstraite <xref:System.Windows.Media.Animation.Timeline> les objets qui génèrent des valeurs de sortie pour animer des propriétés.|  
|<xref:System.Windows.Media.MediaTimeline>|Génère une sortie à partir d’un fichier multimédia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Un type de <xref:System.Windows.Media.Animation.TimelineGroup> que les groupes et des contrôles enfants <xref:System.Windows.Media.Animation.Timeline> objets.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Un type de <xref:System.Windows.Media.Animation.ParallelTimeline> qui fournit des informations de ciblage pour les objets de chronologie qu’il contient.|  
|<xref:System.Windows.Media.Animation.Timeline>|Classe de base abstraite qui définit les comportements de minutage.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Classe abstraite pour <xref:System.Windows.Media.Animation.Timeline> les objets qui peuvent contenir d’autres <xref:System.Windows.Media.Animation.Timeline> objets.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Propriétés qui contrôlent la longueur d’une chronologie  
 A <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps et la longueur d’une chronologie peuvent être décrite de différentes façons. Le tableau suivant définit plusieurs termes servant à décrire la longueur d’une chronologie.  
  
|Terme|Description|Propriétés||||  
|----------|-----------------|----------------|-|-|-|  
|Durée simple|Le temps qu’une chronologie prend pour faire une seule itération vers l’avant.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Une répétition|La durée pendant laquelle il prend une chronologie jouer avant et, si le <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété est true, la lecture d’une fois en arrière.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Période active|La durée pendant laquelle il prend une chronologie compléter toutes les répétitions spécifiées par son <xref:System.Windows.Media.Animation.RepeatBehavior> propriété.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>La propriété Duration  
 Comme indiqué plus haut, une chronologie représente un segment de temps. La longueur de ce segment est déterminée par la chronologie <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Lorsqu’une chronologie atteint la fin de sa durée, elle s’arrête. Si la chronologie a des chronologies enfants, celles-ci s’arrêtent également. Dans le cas d’une animation, la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> spécifie la durée nécessaire à l’animation transition à partir de sa valeur initiale à sa valeur de fin. Durée d’une chronologie est parfois appelée son *durée simple*, pour faire la distinction entre la durée d’une seule itération et la durée totale de l’animation, y compris les répétitions. Vous pouvez spécifier une durée à l’aide d’une valeur de temps finie ou des valeurs spéciales <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>. Durée d’une animation doit se résoudre en un <xref:System.Windows.Duration.TimeSpan%2A> valeur, afin de pouvoir faire la transition entre les valeurs.  
  
 L’exemple suivant montre un <xref:System.Windows.Media.Animation.DoubleAnimation> avec un <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinq secondes.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Les chronologies de conteneur, tel que <xref:System.Windows.Media.Animation.Storyboard> et <xref:System.Windows.Media.Animation.ParallelTimeline>, ont une durée par défaut de <xref:System.Windows.Duration.Automatic%2A>, ce qui signifie qu’elles se terminent automatiquement lorsque leur dernier enfant s’arrête. L’exemple suivant montre un <xref:System.Windows.Media.Animation.Storyboard> dont <xref:System.Windows.Media.Animation.Timeline.Duration%2A> résout à cinq secondes, la durée pendant laquelle elle accepte tous les enfants de son <xref:System.Windows.Media.Animation.DoubleAnimation> objets pour terminer.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 En définissant le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d’une chronologie de conteneur pour un <xref:System.Windows.Duration.TimeSpan%2A> valeur, vous pouvez forcer à jouer plus ou moins de ses enfants <xref:System.Windows.Media.Animation.Timeline> objets. Si vous définissez la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> à une valeur inférieure à la longueur de l’enfant de la chronologie de conteneur <xref:System.Windows.Media.Animation.Timeline> objets, l’enfant <xref:System.Windows.Media.Animation.Timeline> objets s’arrêter lorsque la chronologie de conteneur. L’exemple suivant définit la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de la <xref:System.Windows.Media.Animation.Storyboard> dans les exemples précédents à trois secondes. Par conséquent, la première <xref:System.Windows.Media.Animation.DoubleAnimation> cesse de progresser après trois secondes, lorsqu’elle a animé la largeur du rectangle cible à 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>La propriété RepeatBehavior  
 Le <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété d’un <xref:System.Windows.Media.Animation.Timeline> contrôle le nombre de fois où elle répète sa durée simple. À l’aide de la <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété, vous pouvez spécifier combien de fois la chronologie joue (une itération <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) ou la durée totale qu’elle doit jouer (une répétition <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). Dans les deux cas, l’animation se répète de bout en bout autant de fois qu’il est nécessaire pour respecter la durée ou le nombre imposés. Par défaut, les chronologies ont un nombre d’itérations de `1.0`, ce qui signifie qu’ils jouent qu’une seule fois et ne se répètent pas du tout.  
  
 L’exemple suivant utilise le <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété pour rendre un <xref:System.Windows.Media.Animation.DoubleAnimation> joue deux fois sa durée simple en spécifiant un nombre d’itérations.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 L’exemple suivant utilise le <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété afin que le <xref:System.Windows.Media.Animation.DoubleAnimation> lire la moitié de sa durée simple.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Si vous définissez la <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété d’un <xref:System.Windows.Media.Animation.Timeline> à <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, le <xref:System.Windows.Media.Animation.Timeline> se répète jusqu'à ce que s’est arrêté de façon interactive ou par le système de minuterie. L’exemple suivant utilise le <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété afin que la <xref:System.Windows.Media.Animation.DoubleAnimation> joue indéfiniment.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Pour obtenir un exemple supplémentaire, consultez [répéter une Animation](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>La propriété AutoReverse  
 Le <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété spécifie si un <xref:System.Windows.Media.Animation.Timeline> jouera en arrière à la fin de chaque itération en avant. L’exemple suivant affecte la <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété d’un <xref:System.Windows.Media.Animation.DoubleAnimation> à `true`; par conséquent, il réalise une animation à partir de zéro à 100, puis de 100 à zéro. Elle s’exécute pendant 10 secondes au total.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Lorsque vous utilisez un <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> valeur pour spécifier le <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d’un <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété de ce <xref:System.Windows.Media.Animation.Timeline> est `true`, une répétition unique se compose d’une itération avancée suivie d’un descendante itération.  L’exemple suivant définit la <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> de la <xref:System.Windows.Media.Animation.DoubleAnimation> à partir de l’exemple précédent pour un <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> de deux. Par conséquent, la <xref:System.Windows.Media.Animation.DoubleAnimation> joue pendant 20 secondes : transférer pour transférer les cinq secondes, en arrière pendant cinq secondes, pendant 5 secondes, puis en arrière pendant cinq secondes.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Si une chronologie de conteneur a des enfants <xref:System.Windows.Media.Animation.Timeline> des objets, ils inversent lors de la chronologie de conteneur. Pour obtenir des exemples supplémentaires, consultez [spécifier si une chronologie inverse automatiquement](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>La propriété BeginTime  
 Le <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriété vous permet de spécifier quand une chronologie démarre.  Le temps de début d’une chronologie est relatif à la chronologie de son parent. Un temps de début de zéro seconde signifie que la chronologie démarre dès que son parent démarre ; toute autre valeur crée un décalage entre le démarrage de la chronologie parent et celui de la chronologie enfant. Par exemple, un temps de début de deux secondes signifie que la chronologie démarre quand son parent a atteint une durée de deux secondes. Par défaut, toutes les chronologies ont un temps de début de zéro seconde. Vous pouvez également définir une chronologie commencer de temps `null`, ce qui empêche la chronologie de démarrer. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous spécifiez la valeur null à l’aide de la [x : Null, Extension de balisage](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
 Notez que l’heure de début n’est pas appliquée à chaque fois qu’une chronologie se répète raison de son <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> paramètre. Si vous deviez créer une animation avec une <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> de 10 secondes et un <xref:System.Windows.Media.Animation.RepeatBehavior> de <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, il serait un délai de 10 secondes avant que l’animation lue pour la première fois, mais pas pour chaque répétition successive. Toutefois, si la chronologie du parent de l’animation devait redémarrer ou se répéter, le délai de 10 secondes se produirait.  
  
 Le <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriété est utile pour échelonner les chronologies. L’exemple suivant crée un <xref:System.Windows.Media.Animation.Storyboard> qui a deux enfants <xref:System.Windows.Media.Animation.DoubleAnimation> objets. La première animation a une <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinq secondes, et la seconde a un <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de 3 secondes. L’exemple définit le <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> du deuxième <xref:System.Windows.Media.Animation.DoubleAnimation> à 5 secondes, par conséquent, qu’elle démarre après la première <xref:System.Windows.Media.Animation.DoubleAnimation> se termine.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>La propriété FillBehavior  
 Lorsqu’un <xref:System.Windows.Media.Animation.Timeline> atteint la fin de sa durée active totale, la <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété indique s’il s’arrête ou maintient sa dernière valeur. Une animation avec une <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> « contient « sa valeur de sortie : la propriété animée conserve la dernière valeur de l’animation. La valeur <xref:System.Windows.Media.Animation.FillBehavior.Stop> qui provoque l’arrêt de l’animation affecter sa propriété cible après la fin.  
  
 L’exemple suivant crée un <xref:System.Windows.Media.Animation.Storyboard> qui a deux enfants <xref:System.Windows.Media.Animation.DoubleAnimation> objets. Les deux <xref:System.Windows.Media.Animation.DoubleAnimation> animent des objets le <xref:System.Windows.FrameworkElement.Width%2A> d’un <xref:System.Windows.Shapes.Rectangle> de 0 à 100. Le <xref:System.Windows.Shapes.Rectangle> éléments ont non animée <xref:System.Windows.FrameworkElement.Width%2A> valeurs 500 [pixels indépendants du périphérique].  
  
-   Le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété du premier <xref:System.Windows.Media.Animation.DoubleAnimation> a la valeur <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, la valeur par défaut. Par conséquent, la largeur du Rectangle reste à 100 après la <xref:System.Windows.Media.Animation.DoubleAnimation> se termine.  
  
-   Le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété du deuxième <xref:System.Windows.Media.Animation.DoubleAnimation> a la valeur <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Par conséquent, le <xref:System.Windows.FrameworkElement.Width%2A> du deuxième <xref:System.Windows.Shapes.Rectangle> revient à 500 après le <xref:System.Windows.Media.Animation.DoubleAnimation> se termine.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Propriétés qui contrôlent la vitesse d’une chronologie  
 La <xref:System.Windows.Media.Animation.Timeline> classe fournit trois propriétés pour spécifier sa vitesse :  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>: Spécifie que les taux, par rapport à son parent, à laquelle progresse le temps pour un <xref:System.Windows.Media.Animation.Timeline>. Valeurs supérieures à un augmentent la vitesse de la <xref:System.Windows.Media.Animation.Timeline> et de ses enfants <xref:System.Windows.Media.Animation.Timeline> objets ; les valeurs comprises entre zéro et un ralentissent. Une valeur d’un indique que <xref:System.Windows.Media.Animation.Timeline> progresse à la même vitesse que son parent. Le <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> paramètre d’une chronologie de conteneur affecte tous ses enfants <xref:System.Windows.Media.Animation.Timeline> également des objets.  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>: Indique le pourcentage de la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d’une chronologie consacré à l’accélération. Pour obtenir un exemple, consultez [Comment : accélérer ou ralentir une Animation](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md). 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>-Spécifie le pourcentage de la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d’une chronologie à la décélération. Pour obtenir un exemple, consultez [Comment : accélérer ou ralentir une Animation](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Vue d'ensemble des événements de minuterie](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Comportement de minuterie d’animation exemple](http://go.microsoft.com/fwlink/?LinkID=159970)
