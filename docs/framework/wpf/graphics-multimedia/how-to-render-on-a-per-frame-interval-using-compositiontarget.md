---
title: "Comment : effectuer une restitution par intervalle de trame à l'aide de CompositionTarget"
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
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7616a418b9f2f6b175b925e4385322c42546e9bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Comment : effectuer une restitution par intervalle de trame à l'aide de CompositionTarget
Le moteur d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit de nombreuses fonctionnalités qui permettent de créer une animation à partir d’une trame. Il existe cependant des scénarios d’application dans lesquels vous devez affiner le rendu trame par trame. Le <xref:System.Windows.Media.CompositionTarget> objet permet de créer des animations personnalisées en fonction de rappel image par image.  
  
 <xref:System.Windows.Media.CompositionTarget>est une classe statique qui représente la surface d’affichage sur laquelle votre application est dessinée. Le <xref:System.Windows.Media.CompositionTarget.Rendering> événement est déclenché chaque fois que la scène de l’application est dessinée. La fréquence d’images de rendu représente le nombre de fois que la scène est dessinée par seconde.  
  
> [!NOTE]
>  Pour un exemple de code complet à l’aide de <xref:System.Windows.Media.CompositionTarget>, consultez [à l’aide de l’exemple de classe CompositionTarget](http://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Exemple  
 Le <xref:System.Windows.Media.CompositionTarget.Rendering> événement est déclenché lors de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processus de rendu. L’exemple suivant montre comment inscrire une <xref:System.EventHandler> déléguer à la méthode statique <xref:System.Windows.Media.CompositionTarget.Rendering> méthode sur <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Vous pouvez utiliser la méthode de votre gestionnaire d’événements de rendu pour créer un contenu de dessin personnalisé. Cette méthode de gestionnaire d’événements est appelée une fois par image. Chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l’arborescence visuelle sur le graphique de la scène de composition, votre méthode de gestionnaire d’événements est appelée. En outre, si les modifications apportées à l’arborescence visuelle forcent les mises à jour sur le graphique de la scène de composition, votre méthode de gestionnaire d’événements est également appelée. Notez que votre méthode de gestionnaire d’événements est appelée une fois la disposition calculée. Vous pouvez cependant modifier la disposition dans votre méthode de gestionnaire d’événements, de sorte que cette disposition soit calculée avant le rendu.  
  
 L’exemple suivant montre comment vous pouvez fournir dessin personnalisé dans un <xref:System.Windows.Media.CompositionTarget> méthode de gestionnaire d’événements. Dans ce cas, la couleur d’arrière-plan de la <xref:System.Windows.Controls.Canvas> est dessiné avec une valeur de couleur en fonction de la position des coordonnées de la souris. Si vous déplacez la souris à l’intérieur de la <xref:System.Windows.Controls.Canvas>, sa couleur d’arrière-plan change. En outre, la fréquence d’images moyenne est calculée en fonction du temps écoulé actuel et du nombre total de trames rendues.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Vous pouvez voir que votre dessin personnalisé s’exécute à des vitesses différentes selon l’ordinateur utilisé. En effet, votre dessin personnalisé est dépendant de la fréquence d’images. Selon le système que vous exécutez et la charge de travail de ce système, le <xref:System.Windows.Media.CompositionTarget.Rendering> événement peut être appelé plusieurs fois par seconde. Pour savoir comment déterminer les capacités et les performances du matériel graphique pour un appareil qui exécute une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez la page [Couches de rendu graphiques](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 Ajout ou suppression d’un rendu <xref:System.EventHandler> délégué pendant le déclenchement de l’événement sera différé jusqu'à la fin de l’événement déclencher. Cela est cohérent avec la <xref:System.MulticastDelegate>-basé sur les événements sont gérés dans le Common Language Runtime (CLR). Notez également que les événements de rendu ne sont pas forcément appelés dans un ordre particulier. Si vous disposez de plusieurs <xref:System.EventHandler> délégués qui reposent sur un ordre particulier, vous devez inscrire un seul <xref:System.Windows.Media.CompositionTarget.Rendering> événement et multiplexer les délégués dans le bon de commande vous-même.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.CompositionTarget>  
 [Vue d’ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
