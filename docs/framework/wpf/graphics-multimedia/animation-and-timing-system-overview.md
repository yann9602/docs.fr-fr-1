---
title: "Vue d&#39;ensemble de l&#39;animation et du syst&#232;me de minutage | Microsoft Docs"
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
  - "animation (WPF)"
  - "minuterie (système) (WPF)"
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble de l&#39;animation et du syst&#232;me de minutage
Cette rubrique décrit comment le système d'horloge utilise l'animation et les classes <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Clock> pour animer des propriétés.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## Composants requis  
 Pour comprendre cette rubrique, vous devez être en mesure d'utiliser des animations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour animer des propriétés, comme décrit dans [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  Cette rubrique vous aide également à vous familiariser avec les [propriétés de dépendance](GTMT) ; pour plus d'informations, consultez le [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>   
## Chronologies et horloges  
 L' [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a décrit comment une <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps, et une animation un type de <xref:System.Windows.Media.Animation.Timeline> qui produit des valeurs de sortie.  Une <xref:System.Windows.Media.Animation.Timeline>, par définition, ne fait rien d'autre que de décrire un segment de temps.  C'est l'objet <xref:System.Windows.Media.Animation.Clock> de la chronologie qui fait le vrai travail.  De la même façon, l'animation n'anime pas réellement de propriétés : une classe d'animation décrit comment les valeurs de sortie doivent être calculées, mais c'est l'<xref:System.Windows.Media.Animation.Clock> créée pour l'animation qui achemine la sortie d'animation et l'applique aux propriétés.  
  
 Une <xref:System.Windows.Media.Animation.Clock> est un type spécial d'objet qui conserve l'état de l'horloge au moment de l'exécution pour la <xref:System.Windows.Media.Animation.Timeline>.  Il fournit trois bits des informations qui sont essentielles à l'animation et au système d'horodatage : <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>, <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A> et <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>.  Une <xref:System.Windows.Media.Animation.Clock> détermine son temps réel, sa progression et son état en utilisant les comportements d'horloge décrit par son <xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, et ainsi de suite.  
  
 Dans la plupart des cas, une <xref:System.Windows.Media.Animation.Clock> est créée automatiquement pour votre chronologie.  Lorsque vous animez en utilisant un <xref:System.Windows.Media.Animation.Storyboard> ou la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>, les horloges sont créées automatiquement pour vos chronologies et animations et appliquées à leurs propriétés ciblées.  Vous pouvez également créer une <xref:System.Windows.Media.Animation.Clock> de manière explicite à l'aide de la méthode <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> de votre <xref:System.Windows.Media.Animation.Timeline>.  La méthode <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=fullName> crée une horloge du type approprié pour la <xref:System.Windows.Media.Animation.Timeline> sur laquelle elle est appelée.  Si la <xref:System.Windows.Media.Animation.Timeline> contient des chronologies enfants, elle crée également des objets <xref:System.Windows.Media.Animation.Clock> pour ces dernières.  Les objets <xref:System.Windows.Media.Animation.Clock> résultants sont disposés en arborescences qui correspondent à la structure de l'arborescence d'objets <xref:System.Windows.Media.Animation.Timeline> à partir de laquelle ils sont créés.  
  
 Il existe différents types d'horloges pour les types différents de chronologies.  La table suivante affiche les types <xref:System.Windows.Media.Animation.Clock> qui correspondent à certains des différents types <xref:System.Windows.Media.Animation.Timeline>.  
  
|Type de chronologie|Type d'horloge|Objectif de l'horloge|  
|-------------------------|--------------------|---------------------------|  
|Animation \(hérite de <xref:System.Windows.Media.Animation.AnimationTimeline>\)|<xref:System.Windows.Media.Animation.AnimationClock>|Génère des valeurs de sortie pour une propriété de dépendance.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Traite un fichier multimédia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Groupe et contrôle ses objets <xref:System.Windows.Media.Animation.Clock> enfants|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Groupe et contrôle ses objets <xref:System.Windows.Media.Animation.Clock> enfants|  
  
 Vous pouvez appliquer tous les objets <xref:System.Windows.Media.Animation.AnimationClock> que vous créez aux propriétés de dépendance compatibles en utilisant la méthode <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A>.  
  
 Dans les scénarios aux performance intensives, tels que l'animation d'un grand nombre d'objets semblables, la gestion de votre propre utilisation de <xref:System.Windows.Media.Animation.Clock> peut fournir des avantages en matière de performances.  
  
<a name="timemanager"></a>   
## Horloges et Gestionnaire de temps  
 Lorsque vous animez des objets dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], c'est le gestionnaire de temps qui gère les objets <xref:System.Windows.Media.MediaPlayer.Clock%2A> créés pour vos chronologies.  Le gestionnaire de temps est la racine d'une arborescence d'objets <xref:System.Windows.Media.MediaPlayer.Clock%2A> et contrôle le flux de temps dans cette arborescence.  Un gestionnaire de temps est créé automatiquement pour chaque application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et reste invisible au développeur d'applications. Le gestionnaire de temps "fait tic\-tac" plusieurs fois par seconde ; le nombre réel des battements qui se produisent chaque seconde varie selon les ressources système disponibles.  Pendant chacun de ces battements, le gestionnaire de temps calcule l'état de tous les objets <xref:System.Windows.Media.Animation.ClockState><xref:System.Windows.Media.Animation.Clock>dans l'arborescence de temps.  
  
 L'illustration suivante montre la relation entre le gestionnaire de temps et <xref:System.Windows.Media.Animation.AnimationClock>, et une propriété de dépendance animée.  
  
 ![Composants du système de minuterie](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-1clock1prop.png "graphicsmm\_clocks\_1clock1prop")  
Animer une propriété  
  
 Lorsque le gestionnaire de temps fait tic\-tac, il met à jour l'heure de chaque <xref:System.Windows.Media.Animation.ClockState><xref:System.Windows.Media.Animation.Clock> dans l'application.  Si l'<xref:System.Windows.Media.Animation.Clock> est une <xref:System.Windows.Media.Animation.AnimationClock>, elle utilise la méthode <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> de la <xref:System.Windows.Media.Animation.AnimationTimeline> à partir de laquelle est a été créée pour calculer sa valeur de sortie réelle.  L'<xref:System.Windows.Media.Animation.AnimationClock> donne à la <xref:System.Windows.Media.Animation.AnimationTimeline> l'heure locale actuelle, une valeur d'entrée, qui est en général la valeur de base de la propriété et une valeur de destination par défaut.  Lorsque vous récupérez la valeur d'un animé par propriété à l'aide de la méthode <xref:System.Windows.DependencyObject.GetValue%2A> ou de son accesseur CLR, vous obtenez la sortie de son <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### Groupes d'horloges  
 La section précédente a décrit les différents types d'objets <xref:System.Windows.Media.Animation.Clock> pour différents types de chronologies.  L'illustration suivante montre la relation entre le gestionnaire de temps, un <xref:System.Windows.Media.Animation.ClockGroup>, une <xref:System.Windows.Media.Animation.AnimationClock>, et une propriété de dépendance animée.  Un <xref:System.Windows.Media.Animation.ClockGroup> est créé pour les chronologies qui groupent d'autres chronologies, telles que la classe <xref:System.Windows.Media.Animation.Storyboard> qui groupe des animations et d'autres chronologies.  
  
 ![Composants du système de minuterie](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm\_clocks\_2clock1clockgroup2prop")  
Un groupe d'horloges  
  
#### Composition  
 Il est possible d'associer plusieurs horloges à une propriété unique, auquel cas chaque horloge utilise la valeur de sortie de l'horloge précédente comme sa valeur de base.  L'illustration suivante montre trois objets <xref:System.Windows.Media.Animation.AnimationClock> appliqués à la même propriété.  L'horloge1 utilise la valeur de base de la propriété animée comme son entrée et l'utilise pour générer la sortie.  L'horloge2 prend la sortie de l'horloge1 comme son entrée et l'utilise pour générer la sortie.  L'horloge3 prend la sortie de l'horloge2 comme son entrée et l'utilise pour générer la sortie.  Lorsque plusieurs horloges affectent la même propriété simultanément, ils sont considérés comme étant dans une chaîne de composition.  
  
 ![Composants du système de minuterie](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1prop.png "graphicsmm\_clocks\_2clock1prop")  
Une chaîne de composition  
  
 Notez que bien qu'une relation soit créée parmi l'entrée et la sortie des objets <xref:System.Windows.Media.Animation.AnimationClock> dans la chaîne de composition, leurs comportements d'horloge ne sont pas affectés ; les objets <xref:System.Windows.Media.Animation.Clock> \(y compris les objets <xref:System.Windows.Media.Animation.AnimationClock>\) ont une dépendance hiérarchique sur leurs objets <xref:System.Windows.Media.Animation.Clock> parents.  
  
 Pour appliquer plusieurs horloges à la même propriété, utilisez le <xref:System.Windows.Media.Animation.HandoffBehavior><xref:System.Windows.Media.Animation.HandoffBehavior>lors de l'application d'un <xref:System.Windows.Media.Animation.Storyboard>, d'une animation ou <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### Consolidation de battements et d'événement  
 En plus de calculer des valeurs de sortie, le gestionnaire de temps effectue un autre travail à chaque battement : il détermine l'état de chaque horloge et déclenche les événements appropriés.  
  
 Alors que les battements se produisent fréquemment, il est possible que beaucoup de choses se passent entre les battements.  Par exemple, une <xref:System.Windows.Media.Animation.Clock> peut être arrêtée, démarrée, arrêtée à nouveau, auquel cas sa valeur <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> sera modifié trois fois.  En théorie, l'événement <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> pourrait être déclenché plusieurs fois dans un battement unique ; toutefois, le moteur de minutage consolide les événements, afin que l'événement <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> puisse être déclenché au plus une fois par battement.  Ceci est vrai pour tous les événements d'horloge : un événement de chaque type au plus est déclenché pour un objet <xref:System.Windows.Media.Animation.Clock> donné.  
  
 Lorsqu'une <xref:System.Windows.Media.Animation.Clock> change d'état et revient à son état d'origine entre les battements \(comme passer de <xref:System.Windows.Media.Animation.ClockState> à <xref:System.Windows.Media.Animation.ClockState> puis de nouveau à <xref:System.Windows.Media.Animation.ClockState>\), l'événement associé se produit encore.  
  
 Pour plus d'informations sur les événements d'horloge, consultez [Vue d'ensemble des événements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## Valeurs actuelles et valeurs de base des propriétés  
 Une propriété pouvant être animée peut avoir deux valeurs : une valeur de base et une valeur réelle.  Lorsque vous définissez une propriété à l'aide de son accesseur CLR ou la méthode <xref:System.Windows.DependencyObject.SetValue%2A>, vous définissez sa valeur de base.  Lorsqu'une propriété n'est pas animée, ses valeurs de base et réelles sont identiques.  
  
 Lorsque vous animez une propriété, le <xref:System.Windows.Media.Animation.AnimationClock> définit la valeur *réelle* de la propriété.  La récupération de la valeur de la propriété par le biais de son accesseur CLR ou de la méthode <xref:System.Windows.DependencyObject.GetValue%2A> renvoie la sortie du <xref:System.Windows.Media.Animation.AnimationClock> lorsque le <xref:System.Windows.Media.Animation.AnimationClock> est <xref:System.Windows.Media.Animation.ClockState> ou <xref:System.Windows.Media.Animation.ClockState>.  Vous pouvez récupérer la valeur de base de la propriété à l'aide de la méthode <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A>.  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des événements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)   
 [Vue d'ensemble des comportements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)