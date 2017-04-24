---
title: "Vue d&#39;ensemble du multim&#233;dia | Microsoft Docs"
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
  - "média"
  - "multimédias"
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Vue d&#39;ensemble du multim&#233;dia
Les fonctionnalités multimédias de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permettent d'intégrer de l'audio et de la vidéo dans vos applications afin d'améliorer l'expérience de l'utilisateur. Cette rubrique présente les fonctionnalités multimédias de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
   
  
<a name="mediaapi"></a>   
## API de médias  
 Les classes <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Media.MediaPlayer> proposent du contenu audio et vidéo.  Ces classes peuvent être contrôlées interactivement ou par une horloge.  Ces classes peuvent utilisées les contrôles du [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 pour la lecture multimédia. La classe que vous utilisez dépend du scénario.  
  
 <xref:System.Windows.Controls.MediaElement> est un <xref:System.Windows.UIElement> qui est pris en charge par [Disposition](../../../../docs/framework/wpf/advanced/layout.md) et peut être consommé en tant que contenu de nombreux contrôles.  Il peut être utilisé en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme dans le code. <xref:System.Windows.Media.MediaPlayer>, en revanche, est conçu pour les objets <xref:System.Windows.Media.Drawing> et ne prend pas en charge la disposition.  Les médias chargés à l'aide d'un <xref:System.Windows.Media.MediaPlayer> peuvent être présentés uniquement à l'aide d'un <xref:System.Windows.Media.VideoDrawing> ou en interagissant directement avec un <xref:System.Windows.Media.DrawingContext>.  <xref:System.Windows.Media.MediaPlayer> est inutilisable en XAML.  
  
 Pour plus d'informations sur les objets dessin et le contexte de dessin, consultez [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
> [!NOTE]
>  Lorsque vous distribuez du média avec votre application, vous ne pouvez pas utiliser un fichier multimédia comme ressource de projet.  Dans votre fichier projet, vous devez plutôt affecter `Content` au type de média et `PreserveNewest` ou `Always` à `CopyToOutputDirectory`.  
  
<a name="mediaplaybackmodes"></a>   
## Modes de lecture de médias  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Media.MediaPlayer> ont tous deux des membres similaires.  Les liens de cette section se rapportent aux membres de la classe <xref:System.Windows.Controls.MediaElement>.  Sauf indication contraire, les membres qui sont liés dans la classe <xref:System.Windows.Controls.MediaElement> se trouvent également dans la classe <xref:System.Windows.Media.MediaPlayer>.  
  
 Pour comprendre la lecture des médias dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], il est nécessaire de comprendre les différents modes de lecture des médias.  <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Media.MediaPlayer> peuvent tous deux être utilisés dans deux modes de médias différents, le mode indépendant et le mode horloge.  Le mode de média est déterminé par la propriété <xref:System.Windows.Controls.MediaElement.Clock%2A>.  Lorsque <xref:System.Windows.Controls.MediaElement.Clock%2A> a la valeur `null`, l'objet média est en mode indépendant.  Lorsque le <xref:System.Windows.Controls.MediaElement.Clock%2A> n'a pas la valeur null, l'objet média est en mode horloge.  Par défaut, les objets médias sont en mode indépendant.  
  
### Mode indépendant  
 En mode indépendant, le contenu du média détermine la lecture du média.  Le mode indépendant prend en charge les options suivantes :  
  
-   L'<xref:System.Uri> du média peut être directement spécifié.  
  
-   La lecture du média peut être directement contrôlée.  
  
-   Les propriétés <xref:System.Windows.Controls.MediaElement.Position%2A> et <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> du média peuvent être modifiées.  
  
 Pour charger le média, définissez la propriété <xref:System.Windows.Controls.MediaElement.Source%2A> de l'objet <xref:System.Windows.Controls.MediaElement> ou appelez la méthode <xref:System.Windows.Media.MediaPlayer.Open%2A> de l'objet <xref:System.Windows.Media.MediaPlayer>.  
  
 Pour contrôler la lecture du média en mode indépendant, utilisez les méthodes de contrôle de l'objet média.  Les méthodes de contrôle qui sont disponibles sont <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A> et <xref:System.Windows.Controls.MediaElement.Stop%2A>.  Pour <xref:System.Windows.Controls.MediaElement>, le contrôle interactif à l'aide de ces méthodes est uniquement disponible lorsque le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a la valeur <xref:System.Windows.Controls.MediaState>.  Ces méthodes ne sont pas disponibles lorsque l'objet média est en mode horloge.  
  
 Pour obtenir un exemple de mode indépendant, consultez [Contrôler un MediaElement \(lecture, pause, arrêt, volume et vitesse\)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md).  
  
### Mode horloge  
 En mode horloge, un <xref:System.Windows.Media.MediaTimeline> détermine la lecture du média.  Le mode horloge présente les caractéristiques suivantes :  
  
-   L'<xref:System.Uri> du média est indirectement défini via un <xref:System.Windows.Media.MediaTimeline>.  
  
-   La lecture du média peut être contrôlée par l'horloge.  Les méthodes de contrôle de l'objet média ne peuvent pas être utilisées.  
  
-   Pour charger le média, définissez la propriété <xref:System.Windows.Media.MediaTimeline.Source%2A> d'un objet <xref:System.Windows.Media.MediaTimeline>, créez l'horloge à partir de la chronologie et assignez l'horloge à l'objet média.  Vous pouvez également charger le média de cette manière lorsqu'un <xref:System.Windows.Media.MediaTimeline> à l'intérieur d'un <xref:System.Windows.Media.Animation.Storyboard> a un <xref:System.Windows.Controls.MediaElement> pour cible.  
  
 Pour contrôler la lecture du média en mode horloge, vous devez utiliser les méthodes de contrôle <xref:System.Windows.Media.Animation.ClockController>.  Un <xref:System.Windows.Media.Animation.ClockController> est obtenu à partir de la propriété <xref:System.Windows.Media.Animation.ClockController> du <xref:System.Windows.Media.MediaClock>.  Si vous tentez d'utiliser les méthodes de contrôle d'un objet <xref:System.Windows.Controls.MediaElement> ou <xref:System.Windows.Media.MediaPlayer> en mode horloge, un <xref:System.InvalidOperationException> est levé.  
  
 Pour plus d'informations sur les horloges et les chronologies, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Pour obtenir un exemple de mode horloge, consultez [Contrôler un MediaElement à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md).  
  
<a name="mediaelement"></a>   
## Classe MediaElement  
 Pour ajouter un média à une application, il suffit d'ajouter un contrôle <xref:System.Windows.Controls.MediaElement> à l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l'application et à indiquer un <xref:System.Uri> pour le média que vous souhaitez inclure.  Tous les types de média pris en charge par [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 sont pris en charge dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. L'exemple suivant indique une utilisation simple de <xref:System.Windows.Controls.MediaElement> en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Dans cet exemple, le média fait l'objet d'une lecture automatique dès qu'il est chargé.  Une fois la lecture du média terminée, le média est fermé et toutes les ressources du média sont libérées \(y compris la mémoire vidéo\).  Il s'agit du comportement par défaut de l'objet <xref:System.Windows.Controls.MediaElement> qui est contrôlé par les propriétés <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>.  
  
### Contrôle d'un MediaElement  
 Les propriétés <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> contrôlent le comportement du <xref:System.Windows.Controls.MediaElement> lorsque <xref:System.Windows.FrameworkElement.IsLoaded%2A> a la valeur `true` ou `false` respectivement.  Les propriétés <xref:System.Windows.Controls.MediaState> sont définies de manière à influer sur le comportement de lecture du média.  Par exemple, le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> par défaut est <xref:System.Windows.Controls.MediaState> et l'<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> par défaut est <xref:System.Windows.Controls.MediaState>.  En d'autres termes, dès que le <xref:System.Windows.Controls.MediaElement> est chargé et que le [preroll](GTMT) est terminé, la lecture du média commence.  Une fois la lecture terminée, le média est fermé et toutes les ressources du média sont libérées.  
  
 Les propriétés <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> ne constituent pas le seul mode de contrôle de la lecture du média.  En mode de synchronisation, l'horloge peut contrôler le <xref:System.Windows.Controls.MediaElement> et les méthodes de contrôle interactives ont le contrôle lorsque le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> est <xref:System.Windows.Controls.MediaState>.  <xref:System.Windows.Controls.MediaElement> gère cette compétition pour le contrôle en évaluant les priorités suivantes.  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>.  En place lorsque le média est déchargé.  Toutes les ressources du média sont ainsi assurées d'être libérées par défaut, y compris lorsqu'un <xref:System.Windows.Media.MediaClock> est associé au <xref:System.Windows.Controls.MediaElement>.  
  
2.  <xref:System.Windows.Media.MediaClock>.  En place lorsque le média possède un <xref:System.Windows.Controls.MediaElement.Clock%2A>.  Si le média est déchargé, le <xref:System.Windows.Media.MediaClock> est appliqué tant que l'<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> a la valeur <xref:System.Windows.Controls.MediaState>.  Le mode horloge remplace toujours le comportement chargé du <xref:System.Windows.Controls.MediaElement>.  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>.  En place lorsque le média est chargé.  
  
4.  Les méthodes de contrôle interactives.  En place lorsque <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a la valeur <xref:System.Windows.Controls.MediaState>.  Les méthodes de contrôle qui sont disponibles sont <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A> et <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### Affichage d'un MediaElement  
 Pour afficher un <xref:System.Windows.Controls.MediaElement>, celui\-ci doit avoir du contenu à restituer et ses propriétés <xref:System.Windows.FrameworkElement.ActualWidth%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A> doivent avoir la valeur zéro tant que le contenu est chargé.  Pour le contenu audio uniquement, ces propriétés ont toujours la valeur zéro.  Pour le contenu vidéo, une fois que l'événement <xref:System.Windows.Controls.MediaElement.MediaOpened> a été déclenché, <xref:System.Windows.FrameworkElement.ActualWidth%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A> indiquent la taille du média chargé.  En d'autres termes, tant que le média est chargé, le <xref:System.Windows.Controls.MediaElement> n'occupe aucun espace physique dans l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] à moins que les propriétés <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A> ne soient définies.  
  
 Lorsque les propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> sont toutes les deux définies, le média s'étire pour remplir la zone prévue pour le <xref:System.Windows.Controls.MediaElement>.  Pour conserver les [proportions](GTMT) d'origine du média, la propriété <xref:System.Windows.FrameworkElement.Width%2A> ou la propriété <xref:System.Windows.FrameworkElement.Height%2A> doit être définie, mais pas les deux à la fois.  Lorsque vous définissez à la fois les propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>, le média se présente avec une taille d'élément fixe, ce qui peut ne pas être souhaitable.  
  
 Pour éviter d'obtenir une taille d'élément fixe, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peut exécuter une opération de [preroll](GTMT) sur le média.  Pour ce faire, affectez <xref:System.Windows.Controls.MediaState> ou <xref:System.Windows.Controls.MediaState> à <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>.  Dans le cadre d'un état <xref:System.Windows.Controls.MediaState>, le média fait l'objet d'un preroll et présente le premier frame.  Dans le cadre d'un état <xref:System.Windows.Controls.MediaState>, le média fait l'objet d'un [preroll](GTMT) et sa lecture commence.  
  
<a name="mediaplayer"></a>   
## Classe MediaPlayer  
 Même si la classe <xref:System.Windows.Controls.MediaElement> est un élément de l'infrastructure, la classe <xref:System.Windows.Media.MediaPlayer> est conçue pour être utilisée dans des objets <xref:System.Windows.Media.Drawing>.  Les objets dessin sont utilisés lorsque vous pouvez sacrifier les fonctionnalités du framework afin de gagner en performance ou lorsque vous avez besoin de fonctionnalités <xref:System.Windows.Freezable>.  <xref:System.Windows.Media.MediaPlayer> vous permet de tirer parti de ces fonctionnalités en fournissant du contenu multimédia dans vos applications.  Comme <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> peut être utilisé en mode indépendant ou en mode horloge, mais il est dépourvu de l'état chargé ou déchargé de l'objet <xref:System.Windows.Controls.MediaElement>.  Cela simplifie le contrôle de lecture du <xref:System.Windows.Media.MediaPlayer>.  
  
### Contrôle d'un MediaPlayer  
 Comme <xref:System.Windows.Media.MediaPlayer> est dépourvu d'états, il n'existe que deux moyens de contrôler la lecture du média.  
  
1.  Les méthodes de contrôle interactives.  En place en mode indépendant \(la propriété <xref:System.Windows.Media.MediaPlayer.Clock%2A> a la valeur `null`\).  
  
2.  <xref:System.Windows.Media.MediaClock>.  En place lorsque le média possède un <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### Affichage d'un MediaPlayer  
 Techniquement, un <xref:System.Windows.Media.MediaPlayer> ne peut pas être affiché car il ne possède pas de représentation physique.  Il peut toutefois être utilisé pour présenter le média dans un <xref:System.Windows.Media.Drawing> à l'aide de la classe <xref:System.Windows.Media.VideoDrawing>.  L'exemple suivant montre comment utiliser un <xref:System.Windows.Media.VideoDrawing> pour afficher le média.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour plus d'informations sur les objets <xref:System.Windows.Media.Drawing>, consultez [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.DrawingGroup>   
 [Disposition](../../../../docs/framework/wpf/advanced/layout.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)