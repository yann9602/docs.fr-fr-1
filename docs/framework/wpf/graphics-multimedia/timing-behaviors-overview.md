---
title: "Vue d&#39;ensemble des comportements de minutage | Microsoft Docs"
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
  - "comportements, minutage"
  - "comportements de minutage"
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Vue d&#39;ensemble des comportements de minutage
Cette rubrique décrit les comportements de minutage d'animations et d'autres objets <xref:System.Windows.Media.Animation.Timeline>.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## Composants requis  
 Pour comprendre cette rubrique, vous devez être familiarisé avec les fonctionnalités d'animations de base.  Pour plus d'informations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="timelinetypes"></a>   
## Types de chronologies  
 Une <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps.  Elle fournit des propriétés qui vous permettent de spécifier la longueur de ce segment, lorsqu'il doit démarrer, combien de fois il se répétera, à quelle vitesse progresse le temps dans ce segment, etc.  
  
 Les classes qui héritent de la classe de chronologie proposent d'autres fonctionnalités, telles que la lecture de médias et d'animations.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les types <xref:System.Windows.Media.Animation.Timeline> suivants.  
  
|Type de chronologie|Description|  
|-------------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Classe de base abstraite pour les objets <xref:System.Windows.Media.Animation.Timeline> qui génèrent des valeurs de sortie pour animer des propriétés.|  
|<xref:System.Windows.Media.MediaTimeline>|Génère la sortie d'un fichier multimédia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Un type de <xref:System.Windows.Media.Animation.TimelineGroup> qui regroupe et contrôle des objets <xref:System.Windows.Media.Animation.Timeline> enfants.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Un type de <xref:System.Windows.Media.Animation.ParallelTimeline> qui fournit des informations de ciblage pour les objets de chronologies qu'il contient.|  
|<xref:System.Windows.Media.Animation.Timeline>|Classe de base abstraite qui définit des comportements de minutage.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Classe abstraite pour les objets <xref:System.Windows.Media.Animation.Timeline> qui peuvent contenir d'autres objets <xref:System.Windows.Media.Animation.Timeline>.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## Propriétés qui contrôlent la longueur d'une chronologie  
 Une <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps, et sa longueur peut être décrite de différentes façons.  La table suivante définit plusieurs termes pour décrire la longueur d'une chronologie.  
  
|Terme|Description|Propriétés||||  
|-----------|-----------------|----------------|-|-|-|  
|Durée simple|La durée qu'une chronologie prend pour faire une itération avancée unique.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Une répétition|La durée que prend pour une chronologie pour jouer une fois en avant et, si la propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a la valeur True, pour jouer une fois en arrière.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Période active|La durée que prend une chronologie pour compléter toutes les répétitions spécifiées par sa propriété <xref:System.Windows.Media.Animation.RepeatBehavior>.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### La propriété Durée  
 Comme mentionné ci\-dessus, une chronologie représente un segment de temps.  La longueur de ce segment est déterminée par la <xref:System.Windows.Media.Animation.Timeline.Duration%2A>de la chronologie.  Lorsqu'une chronologie atteint la fin de sa durée, elle arrête de jouer.  Si la chronologie a des chronologies enfants, elles cessent de jouer également.  Dans le cas d'une animation, la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> indique le temps que prend une animation pour passer de sa valeur initiale à sa valeur finale.  La durée d'une chronologie est parfois appelée sa *durée simple*, pour distinguer entre la durée d'une itération unique et la durée totale jouée par animation en tenant compte des répétitions.  Vous pouvez spécifier une durée à l'aide d'une valeur de temps finie ou des valeurs spéciales <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>.  La durée d'une animation doit résoudre à une valeur <xref:System.Windows.Duration.TimeSpan%2A>, afin de pouvoir faire la transition entre les valeurs.  
  
 L'exemple suivant affiche une <xref:System.Windows.Media.Animation.DoubleAnimation> avec une <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinq secondes.  
  
  
  
 Les chronologies de conteneur, telles que <xref:System.Windows.Media.Animation.Storyboard> et <xref:System.Windows.Media.Animation.ParallelTimeline>, ont une durée par défaut de <xref:System.Windows.Duration.Automatic%2A>, ce qui signifie qu'elles se terminent automatiquement lorsque leur dernier enfant arrête de jouer.  L'exemple suivant affiche un <xref:System.Windows.Media.Animation.Storyboard> dont la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> résout à cinq secondes, durée nécessaire pour que tous ses objets enfants <xref:System.Windows.Media.Animation.DoubleAnimation> se terminent.  
  
  
  
 En définissant la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d'une chronologie de conteneur à une valeur de <xref:System.Windows.Duration.TimeSpan%2A>, vous pouvez forcer à jouer plus ou moins longtemps que ses objets enfants <xref:System.Windows.Media.Animation.Timeline>.  Si vous définissez la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> à une valeur qui est plus petite que la longueur des objets enfants <xref:System.Windows.Media.Animation.Timeline> de la chronologie de conteneur, les objets enfants <xref:System.Windows.Media.Animation.Timeline> cessent de jouer en même temps que la chronologie de conteneur.  L'exemple suivant définit la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> du <xref:System.Windows.Media.Animation.Storyboard> des exemples précédents à trois secondes.  En conséquence, la première <xref:System.Windows.Media.Animation.DoubleAnimation> cesse de progresser après trois secondes, lorsqu'elle a animé la largeur du rectangle cible à 60.  
  
  
  
<a name="repeatinganimations"></a>   
### La propriété RepeatBehavior  
 La propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d'une <xref:System.Windows.Media.Animation.Timeline> contrôle le nombre de fois qu'elle répète sa durée simple.  À l'aide de la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, vous pouvez spécifier combien de fois la chronologie joue \(une itération <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>\) ou la durée totale qu'elle doit jouer \(une répétition <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>\).  Dans les deux cas, l'animation est répétée du début à la fin, autant de fois que nécessaire pour répondre à la durée ou au nombre demandé.  Par défaut, le nombre d'itérations des chronologies est `1.0`, ce qui signifie qu'elles ne sont jouées qu'une seule fois.  
  
 L'exemple suivant utilise la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pour qu'une <xref:System.Windows.Media.Animation.DoubleAnimation> joue deux fois sa durée simple en spécifiant un nombre d'itérations.  
  
  
  
 L'exemple suivant utilise la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pour que l'<xref:System.Windows.Media.Animation.DoubleAnimation> joue pour la moitié de sa durée simple.  
  
  
  
 Si vous définissez la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d'une <xref:System.Windows.Media.Animation.Timeline> à <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, la <xref:System.Windows.Media.Animation.Timeline> se répète jusqu'à ce qu'elle soit arrêtée interactivement ou par le système de minutage.  L'exemple suivant utilise la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pour que la <xref:System.Windows.Media.Animation.DoubleAnimation> joue indéfiniment.  
  
  
  
 Pour obtenir un exemple supplémentaire, consultez [Répéter une animation](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### La propriété AutoReverse  
 La propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> indique si <xref:System.Windows.Media.Animation.Timeline> jouera en arrière à la fin de chaque itération avancée.  L'exemple suivant affecte à la propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> de <xref:System.Windows.Media.Animation.DoubleAnimation> la valeur `true`. Par conséquent, elle s'anime de zéro à 100, puis de 100 à zéro.  Elle joue pendant 10 secondes au total.  
  
  
  
 Lorsque vous utilisez une valeur <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> pour spécifier le <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d'une <xref:System.Windows.Media.Animation.Timeline> et que la propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> de cette <xref:System.Windows.Media.Animation.Timeline> a la valeur `true`, une répétition unique se compose d'une itération avancée suivie d'une itération arrière.  L'exemple suivant définit <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> de <xref:System.Windows.Media.Animation.DoubleAnimation> de l'exemple précédent à deux <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>.  En conséquence, la <xref:System.Windows.Media.Animation.DoubleAnimation> joue pendant 20 secondes : en avant pendant cinq secondes, en arrière pendant cinq secondes, en avant pendant encore pour cinq secondes, puis en arrière pendant cinq secondes.  
  
  
  
 Si une chronologie de conteneur a des objets enfants <xref:System.Windows.Media.Animation.Timeline>, ils s'inversent en même temps que la chronologie de conteneur.  Pour obtenir d'autres exemples, consultez [Spécifier l'inversion automatique ou non d'une chronologie](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## La propriété BeginTime  
 La propriété <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> vous permet de spécifier quand une chronologie démarre.  L'heure de début d'une chronologie est relative à sa chronologie parente.  Une heure de début de zéro seconde signifie que la chronologie démarre dès son parent démarre ; toute autre valeur crée un offset entre le moment où la chronologie parente commence à jouer et le moment où la chronologie enfant joue.  Par exemple, une heure de début de deux secondes signifie que la chronologie commence à jouer lorsque son parent a atteint une durée de deux secondes.  Par défaut, toutes les chronologies ont une heure de début de zéro seconde.  Vous pouvez également définir l'heure de début d'une chronologie à `null`, ce qui empêche la chronologie de démarrer.  Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous indiquez zéro en utilisant [x:Null, extension de balisage](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
 Notez que l'heure de début n'est pas appliquée à chaque fois qu'une chronologie se répète en raison de son paramètre <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.  Si vous deviez créer une animation avec une <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> de 10 secondes et un <xref:System.Windows.Media.Animation.RepeatBehavior> de <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, il y aurait un délai de 10 secondes avant que l'animation ne joue pour la première fois, mais pas pour chaque répétition successive.  Toutefois, si la chronologie parente de l'animation devait redémarrer ou se répéter, le délai de 10 secondes se produirait.  
  
 La propriété <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> est utile pour les chronologies graduelles.  L'exemple suivant crée un <xref:System.Windows.Media.Animation.Storyboard> qui a deux objets <xref:System.Windows.Media.Animation.DoubleAnimation> enfants.  La première animation a une <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de 5 secondes, et la seconde a une <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de 3 secondes.  L'exemple définit le <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> de la deuxième <xref:System.Windows.Media.Animation.DoubleAnimation> à 5 secondes, afin qu'elle commence à jouer une fois que la première <xref:System.Windows.Media.Animation.DoubleAnimation> est terminée.  
  
  
  
<a name="fillbehaviorproperty"></a>   
## La propriété FillBehavior  
 Lorsqu'une <xref:System.Windows.Media.Animation.Timeline> atteint la fin de sa durée active totale, la propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> spécifie s'il elle s'arrête ou si elle maintient sa dernière valeur.  Une animation avec un <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior> "conserve" sa valeur de sortie : la propriété qui est animée conserve la dernière valeur de l'animation.  Une valeur de <xref:System.Windows.Media.Animation.FillBehavior> entraîne l'animation à cesser d'affecter sa propriété cible une fois qu'elle est terminée.  
  
 L'exemple suivant crée un <xref:System.Windows.Media.Animation.Storyboard> qui a deux objets <xref:System.Windows.Media.Animation.DoubleAnimation> enfants.  Les objets <xref:System.Windows.Media.Animation.DoubleAnimation> animent le <xref:System.Windows.FrameworkElement.Width%2A> d'un <xref:System.Windows.Shapes.Rectangle> de 0 à 100.  Les éléments <xref:System.Windows.Shapes.Rectangle> ont des valeurs <xref:System.Windows.FrameworkElement.Width%2A> non animées de 500 [dip \(device independent pixels\)](GTMT).  
  
-   La propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> du premier <xref:System.Windows.Media.Animation.DoubleAnimation> a la valeur <xref:System.Windows.Media.Animation.FillBehavior>, la valeur par défaut.  Par conséquent, la largeur du rectangle reste à 100 après la fin de <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
-   La propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> du second <xref:System.Windows.Media.Animation.DoubleAnimation> a la valeur <xref:System.Windows.Media.Animation.FillBehavior>.  Par conséquent, <xref:System.Windows.FrameworkElement.Width%2A> du second <xref:System.Windows.Shapes.Rectangle> revient à 500 après la fin de <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
  
  
<a name="speedproperties"></a>   
## Propriétés qui contrôlent la vitesse d'une chronologie  
 La classe <xref:System.Windows.Media.Animation.Timeline> fournit trois propriétés pour spécifier sa vitesse :  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>. Spécifie la vitesse, par rapport à son parent, à laquelle progresse le temps pour une <xref:System.Windows.Media.Animation.Timeline>.  Les valeurs supérieures à un augmentent la vitesse des <xref:System.Windows.Media.Animation.Timeline> et de ses objets <xref:System.Windows.Media.Animation.Timeline> enfants ; les valeurs entre zéro et un la ralentissent.  Une valeur de un indique que la <xref:System.Windows.Media.Animation.Timeline> progresse à la même vitesse que son parent.  Le paramètre <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> d'une chronologie de conteneur affecte également tous ses objets <xref:System.Windows.Media.Animation.Timeline> enfants.  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>. Spécifie le pourcentage de <xref:System.Windows.Media.Animation.Timeline.Duration%2A> qu'une chronologie passe à accélérer.  Pour obtenir un exemple, consultez [Accélérer ou décélérer une animation](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md).  
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>. Spécifie le pourcentage de <xref:System.Windows.Media.Animation.Timeline.Duration%2A> qu'une chronologie passe à ralentir.  Pour obtenir un exemple, consultez [Accélérer ou décélérer une animation](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md).  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [Vue d'ensemble des événements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)   
 [Comportement de minutage d'une animation, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159970)