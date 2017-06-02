---
title: "Comment&#160;: effectuer une restitution par intervalle de trame &#224; l&#39;aide de CompositionTarget | Microsoft Docs"
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
  - "objets CompositionTarget, restituer par image"
  - "restituer par image à l'aide d'objets CompositionTarget"
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: effectuer une restitution par intervalle de trame &#224; l&#39;aide de CompositionTarget
Le moteur d'animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propose de nombreuses fonctionnalités permettant de créer une animation par trame.  Toutefois, il existe des scénarios d'application dans lesquels vous avez besoin de mieux contrôler la restitution par trame.  L'objet <xref:System.Windows.Media.CompositionTarget> permet de créer des animations personnalisées sur la base d'un rappel image par image.  
  
 <xref:System.Windows.Media.CompositionTarget> est une classe statique représentant la surface d'affichage sur laquelle votre application est dessinée.  L'événement <xref:System.Windows.Media.CompositionTarget.Rendering> est déclenché chaque fois que la scène de l'application est dessinée.  La fréquence d'images du rendu correspond au nombre de fois que la scène est dessinée par seconde.  
  
> [!NOTE]
>  Pour obtenir un exemple de code complet utilisant <xref:System.Windows.Media.CompositionTarget>, consultez [Utilisation du CompositionTarget, exemple](http://go.microsoft.com/fwlink/?LinkID=160045).  
  
## Exemple  
 L'événement <xref:System.Windows.Media.CompositionTarget.Rendering> est déclenché pendant le processus de restitution [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  L'exemple suivant montre comment inscrire un délégué <xref:System.EventHandler> dans la méthode <xref:System.Windows.Media.CompositionTarget.Rendering> statique de <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Vous pouvez utiliser la méthode du gestionnaire d'événements de rendu pour créer un contenu de dessin personnalisé.  Cette méthode du gestionnaire d'événements est appelée une fois par trame.  À chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l'[arborescence visuelle](GTMT) sur le graphique des scènes de composition, la méthode du gestionnaire d'événements est appelée.  En outre, si des modifications dans l'[arborescence d'éléments visuels](GTMT) forcent la mise à jour du graphique des scènes de composition, votre méthode de gestionnaire d'événements est également appelée.  Notez que votre gestionnaire d'événements est appelé une fois la disposition calculée.  Vous pouvez, toutefois, modifier la disposition dans la méthode de gestionnaire d'événements, auquel cas la disposition sera de nouveau calculée avant le rendu.  
  
 L'exemple suivant indique comment fournir le dessin personnalisé dans une méthode de gestionnaire d'événements <xref:System.Windows.Media.CompositionTarget>.  Dans ce cas, la couleur d'arrière\-plan de <xref:System.Windows.Controls.Canvas> est dessinée avec une valeur de couleur selon la position des coordonnées de la souris.  Si vous déplacez la souris à l'intérieur de <xref:System.Windows.Controls.Canvas>, sa couleur d'arrière\-plan change.  De plus, la fréquence d'images moyenne est calculée, selon le temps écoulé actuel et le nombre total de trames rendues.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Il est possible que vous observiez que votre dessin personnalisé s'exécute à des vitesses différentes sur divers ordinateurs.  Cela est dû au fait que votre dessin personnalisé n'est pas indépendant de la fréquence d'images.  Selon le système que vous exécutez et la charge de travail de ce système, l'événement <xref:System.Windows.Media.CompositionTarget.Rendering> peut être appelé un nombre différent de fois par seconde.  Pour plus d'informations sur la détermination des fonctionnalités matérielles et des performances d'un périphérique exécutant une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Couches de rendu graphiques](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 L'ajout ou la suppression d'un délégué <xref:System.EventHandler> de rendu pendant le déclenchement de l'événement sera différé jusqu'à la fin de ce déclenchement.  Cette approche est cohérente avec la manière dont les événements basés sur <xref:System.MulticastDelegate> sont contrôlés dans CLR \(Common Language Runtime\).  Notez également qu'il n'est pas garanti que les événements de rendu soient appelés dans un ordre particulier.  Si plusieurs délégués <xref:System.EventHandler> comptent sur un ordre particulier, vous devez enregistrer un événement <xref:System.Windows.Media.CompositionTarget.Rendering> unique et multiplexer vous\-même les délégués dans l'ordre approprié.  
  
## Voir aussi  
 <xref:System.Windows.Media.CompositionTarget>   
 [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)