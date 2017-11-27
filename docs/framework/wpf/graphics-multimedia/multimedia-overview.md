---
title: "Vue d'ensemble du multimédia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7097f5bd58573315681c61d0380e58638a4c4fb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="multimedia-overview"></a>Vue d'ensemble du multimédia
Les fonctionnalités multimédias de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permettent d’intégrer des données audio et vidéo dans vos applications afin d’améliorer l’expérience utilisateur. Cette rubrique présente les fonctionnalités multimédias de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 
  
<a name="mediaapi"></a>   
## <a name="media-api"></a>API Media  
 Le <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Media.MediaPlayer> classes sont utilisées pour présenter le contenu audio ou vidéo. Ces classes peuvent être contrôlées interactivement ou par une horloge. Ces classes peuvent être utilisées sur le contrôle [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 pour la lecture multimédia. La classe que vous allez utiliser dépend du scénario.  
  
 <xref:System.Windows.Controls.MediaElement>est un <xref:System.Windows.UIElement> qui est pris en charge par le [disposition](../../../../docs/framework/wpf/advanced/layout.md) et peuvent être utilisés en tant que le contenu de nombreux contrôles. Il est également utilisable en langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ainsi que dans du code. <xref:System.Windows.Media.MediaPlayer>, en revanche, est conçu pour <xref:System.Windows.Media.Drawing> des objets et n’a pas de prise en charge de la mise en page. Support de sauvegarde chargé à l’aide un <xref:System.Windows.Media.MediaPlayer> peut uniquement être présentées à l’aide un <xref:System.Windows.Media.VideoDrawing> ou en interagissant directement avec un <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer>ne peut pas être utilisés en XAML.  
  
 Pour plus d’informations sur les objets de dessin et le contexte de dessin, consultez [Vue d’ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
> [!NOTE]
>  Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet. Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Modes de lecture de médias  
  
> [!NOTE]
>  Les deux <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Media.MediaPlayer> ont des membres semblables. Les liens de cette section font référence à la <xref:System.Windows.Controls.MediaElement> membres de classe. Sauf mention contraire, les membres sont liés dans le <xref:System.Windows.Controls.MediaElement> classe figurent également dans la <xref:System.Windows.Media.MediaPlayer> classe.  
  
 Pour comprendre la lecture de médias dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], il est nécessaire de comprendre les différents modes de lecture des médias. Les deux <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Media.MediaPlayer> peut être utilisé dans deux modes différents médias, mode indépendant et le mode d’horloge. Le mode de média est déterminé par le <xref:System.Windows.Controls.MediaElement.Clock%2A> propriété. Lorsque <xref:System.Windows.Controls.MediaElement.Clock%2A> est `null`, l’objet média est en mode indépendant. Lorsque le <xref:System.Windows.Controls.MediaElement.Clock%2A> est non null, l’objet média est en mode horloge. Par défaut, les objets médias sont en mode indépendant.  
  
### <a name="independent-mode"></a>Mode indépendant  
 En mode indépendant, le contenu du média déclenche la lecture du média. Le mode indépendant comprend les options suivantes :  
  
-   De support <xref:System.Uri> peut être spécifiée directement.  
  
-   La lecture du média peut être directement contrôlée.  
  
-   De support <xref:System.Windows.Controls.MediaElement.Position%2A> et <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> propriétés peuvent être modifiées.  
  
 Charger le média soit en définissant le <xref:System.Windows.Controls.MediaElement> l’objet <xref:System.Windows.Controls.MediaElement.Source%2A> propriété ou en appelant le <xref:System.Windows.Media.MediaPlayer> l’objet <xref:System.Windows.Media.MediaPlayer.Open%2A> (méthode).  
  
 Pour contrôler la lecture du média en mode indépendant, les méthodes de contrôle de l’objet média peuvent être utilisées. Les méthodes de contrôle disponibles sont <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, et <xref:System.Windows.Controls.MediaElement.Stop%2A>. Pour <xref:System.Windows.Controls.MediaElement>, un contrôle interactif à l’aide de ces méthodes est disponible uniquement lorsque le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a la valeur <xref:System.Windows.Controls.MediaState.Manual>. Ces méthodes ne sont pas disponibles lorsque l’objet média est en mode horloge.  
  
 Consultez la page [Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) pour obtenir un exemple de mode indépendant.  
  
### <a name="clock-mode"></a>Mode horloge  
 En mode horloge, une <xref:System.Windows.Media.MediaTimeline> la lecture du média des lecteurs. Le mode horloge présente les caractéristiques suivantes :  
  
-   De support <xref:System.Uri> est indirectement défini via un <xref:System.Windows.Media.MediaTimeline>.  
  
-   La lecture du média peut être contrôlée par l’horloge. Les méthodes de contrôle de l’objet média ne peuvent pas être utilisées.  
  
-   Média est chargé en définissant un <xref:System.Windows.Media.MediaTimeline> l’objet <xref:System.Windows.Media.MediaTimeline.Source%2A> propriété, créez l’horloge à partir de la chronologie et assignez l’horloge à l’objet de support. Également charger le média de cette manière lorsqu’un <xref:System.Windows.Media.MediaTimeline> à l’intérieur d’un <xref:System.Windows.Media.Animation.Storyboard> cibles un <xref:System.Windows.Controls.MediaElement>.  
  
 Pour contrôler la lecture en mode horloge, la <xref:System.Windows.Media.Animation.ClockController> des méthodes de contrôle doivent être utilisées. A <xref:System.Windows.Media.Animation.ClockController> est obtenu à partir de la <xref:System.Windows.Media.Animation.ClockController> propriété de la <xref:System.Windows.Media.MediaClock>. Si vous essayez d’utiliser les méthodes de contrôle d’un <xref:System.Windows.Controls.MediaElement> ou <xref:System.Windows.Media.MediaPlayer> de l’objet en mode horloge, une <xref:System.InvalidOperationException> sera levée.  
  
 Pour plus d’informations sur les horloges et les chronologies, consultez l’article [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Pour obtenir un exemple du mode horloge, consultez la page [Contrôler un MediaElement à l’aide d’un Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md).  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>Classe MediaElement  
 Ajout de médias à une application est aussi simple que l’ajout d’un <xref:System.Windows.Controls.MediaElement> le contrôle à la [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l’application et en fournissant un <xref:System.Uri> sur le média que vous souhaitez inclure. Tous les types de média pris en charge par [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 sont pris en charge dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. L’exemple suivant montre une utilisation simple de la <xref:System.Windows.Controls.MediaElement> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Dans cet exemple, le média est lu automatiquement dès qu’il est chargé. Une fois la lecture du média terminée, le média est fermé et toutes les ressources du média sont libérées (y compris la mémoire vidéo). Il s’agit du comportement par défaut de la <xref:System.Windows.Controls.MediaElement> de l’objet qui est contrôlé par le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriétés.  
  
### <a name="controlling-a-mediaelement"></a>Contrôler un MediaElement  
 Le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriétés contrôlent le comportement de la <xref:System.Windows.Controls.MediaElement> lorsque <xref:System.Windows.FrameworkElement.IsLoaded%2A> est `true` ou `false`, respectivement. Le <xref:System.Windows.Controls.MediaState> les propriétés sont définies pour affecter le comportement de lecture du média. Par exemple, la valeur par défaut <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> est <xref:System.Windows.Controls.MediaState.Play> et la valeur par défaut <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> est <xref:System.Windows.Controls.MediaState.Close>. Cela signifie que, dès le <xref:System.Windows.Controls.MediaElement> est chargé et preroll est terminée, le média commence à lire. Une fois la lecture terminée, le média est fermé et toutes les ressources du média sont libérées.  
  
 Le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriétés ne sont pas la seule façon de contrôler la lecture. En mode horloge, l’horloge peut contrôler le <xref:System.Windows.Controls.MediaElement> et les méthodes de contrôle interactives ont le contrôle lorsque le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> est <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement>gère cette compétition pour le contrôle en évaluant les priorités suivantes.  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Actif lorsque le média est déchargé. Cela garantit que toutes les ressources du média sont libérées par défaut, même si un <xref:System.Windows.Media.MediaClock> est associé le <xref:System.Windows.Controls.MediaElement>.  
  
2.  <xref:System.Windows.Media.MediaClock>. En place lorsque le média possède un <xref:System.Windows.Controls.MediaElement.Clock%2A>. Si le média est déchargé, le <xref:System.Windows.Media.MediaClock> prendra effet tant que la <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> est <xref:System.Windows.Controls.MediaState.Manual>. Mode horloge remplace toujours le comportement chargé du <xref:System.Windows.Controls.MediaElement>.  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Actif lorsque le média est chargé.  
  
4.  Méthodes de contrôle interactives. En place lorsque <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> est <xref:System.Windows.Controls.MediaState.Manual>. Les méthodes de contrôle disponibles sont <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, et <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Afficher un MediaElement  
 Pour afficher un <xref:System.Windows.Controls.MediaElement> il doit avoir un contenu à restituer et elle aura son <xref:System.Windows.FrameworkElement.ActualWidth%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A> propriétés la valeur zéro jusqu'à ce que le contenu est chargé. Pour du contenu purement audio, ces propriétés sont toujours égales à zéro. Pour le contenu vidéo, une fois la <xref:System.Windows.Controls.MediaElement.MediaOpened> événement a été déclenché la <xref:System.Windows.FrameworkElement.ActualWidth%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A> signale à la taille du média chargé. Cela signifie que tant que le média est chargé, le <xref:System.Windows.Controls.MediaElement> n’occupe aucun espace physique dans le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , sauf si le <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A> propriétés sont définies.  
  
 Paramètre à la fois le <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés entraînera le média s’étire pour remplir la zone prévue pour le <xref:System.Windows.Controls.MediaElement>. Pour conserver les proportions du média origine, soit le <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A> la propriété doit être défini mais pas les deux. Paramètre à la fois le <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés entraînera le média se présente avec une taille d’élément fixe qui ne peut pas être souhaitable.  
  
 Pour éviter d’avoir un élément de taille fixe, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peut effectuer un preroll du média. Cela est effectué en définissant le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> soit <xref:System.Windows.Controls.MediaState.Play> ou <xref:System.Windows.Controls.MediaState.Pause>. Dans un <xref:System.Windows.Controls.MediaState.Pause> d’état, le support d’un preroll et présente le premier frame. Dans un <xref:System.Windows.Controls.MediaState.Play> d’état, le support sera preroll et commencer à lire.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Classe MediaPlayer  
 Alors que le <xref:System.Windows.Controls.MediaElement> classe est un élément d’infrastructure, les <xref:System.Windows.Media.MediaPlayer> classe a été conçue pour être utilisée dans <xref:System.Windows.Media.Drawing> objets. Les objets de dessin sont utilisés lorsque vous pouvez sacrifier des fonctionnalités au niveau du framework pour optimiser les performances ou lorsque vous devez <xref:System.Windows.Freezable> fonctionnalités. <xref:System.Windows.Media.MediaPlayer>vous permet de tirer parti de ces fonctionnalités en fournissant le contenu multimédia dans vos applications. Comme <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> peut être utilisé dans indépendante ou d’horloge mode mais ne pas avoir le <xref:System.Windows.Controls.MediaElement> objet déchargé et état chargé. Cela réduit la complexité du contrôle de la lecture de la <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Contrôler un MediaPlayer  
 Étant donné que <xref:System.Windows.Media.MediaPlayer> est sans état, il existe seulement deux façons de contrôler la lecture.  
  
1.  Méthodes de contrôle interactives. En place en mode indépendant (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> propriété).  
  
2.  <xref:System.Windows.Media.MediaClock>. En place lorsque le média possède un <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Afficher un MediaPlayer  
 Techniquement, un <xref:System.Windows.Media.MediaPlayer> ne peut pas être affichée, car elle n’a aucune représentation physique. Toutefois, il peut être utilisé pour présenter le média dans un <xref:System.Windows.Media.Drawing> à l’aide de la <xref:System.Windows.Media.VideoDrawing> classe. L’exemple suivant illustre l’utilisation d’un <xref:System.Windows.Media.VideoDrawing> pour afficher le média.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Consultez le [vue d’ensemble des objets de dessin](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md) pour plus d’informations sur <xref:System.Windows.Media.Drawing> objets.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.DrawingGroup>  
 [Disposition](../../../../docs/framework/wpf/advanced/layout.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
