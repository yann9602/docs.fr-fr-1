---
title: "Aperçu des événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a258a0e145e9a24e6e87bb511fdbd6166422a656
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="preview-events"></a>Aperçu des événements
Événements d’aperçu, également connus sous le tunneling forcé, les événements sont des événements routés où la direction de l’itinéraire se déplace à partir de la racine de l’application vers l’élément qui a déclenché l’événement et est signalé comme étant la source de données d’événement. Pas tous les scénarios d’événement prend en charge ou exiger des événements d’aperçu. Cette rubrique décrit les situations où les événements d’aperçu existent, comment les applications ou les composants doivent les gérer et les cas où la création d’événements d’aperçu dans des composants personnalisés ou des classes peut être appropriée.  
  
## <a name="preview-events-and-input"></a>Événements d’aperçu et entrée  
 Lorsque vous gérez l’aperçu d’événements, en général, soyez prudent quant à marquer les événements gérés événements dans les données. Gestion d’un événement de la version d’évaluation sur tout élément autre que l’élément qui l’a déclenché (l’élément qui est signalé comme source dans les données d’événement) a pour effet de ne pas fournir un élément de la possibilité de gérer l’événement qu’il a. Parfois, voici le résultat souhaité, en particulier si l’élément en question existe dans des relations dans la composition d’un contrôle.  
  
 Pour les événements d’entrée en particulier, les événements d’aperçu également partagent instances de données d’événement avec l’événement de propagation équivalent. Si vous utilisez un gestionnaire de classe d’événements Aperçu pour marquer l’événement d’entrée géré, le Gestionnaire de classe d’événements d’entrée propagation ne sera pas appelé. Ou, si vous utilisez un gestionnaire d’instance événements Aperçu pour marquer l’événement géré, gestionnaires pour l’événement de propagation ne seront pas généralement appelées. Gestionnaires de classe ou les gestionnaires d’instance peuvent être inscrit ou attachés avec une option à appeler même si l’événement est marqué comme géré, mais cette technique n’est pas couramment utilisé.  
  
 Pour plus d’informations sur la gestion de classe et sa relation avec les événements d’aperçu consultez [le marquage des événements routés comme Handled et de gestion de la classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
### <a name="working-around-event-suppression-by-controls"></a>Résolution des problèmes liés à la suppression d’événements par des contrôles  
 Un scénario où les événements d’aperçu sont couramment utilisées est pour la gestion de contrôle composite d’événements d’entrée. Dans certains cas, l’auteur du contrôle supprime un certain événement d’origine à partir de leur contrôle, peut-être pour remplacer un événement défini par le composant qui comporte plus d’informations ou implique un comportement plus spécifique. Par exemple, un [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> supprime <xref:System.Windows.UIElement.MouseLeftButtonDown> et <xref:System.Windows.UIElement.MouseLeftButtonDown> propagation des événements déclenchés par le <xref:System.Windows.Controls.Button> ou ses éléments composites en faveur de la capture de la souris et le déclenchement d’un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement est toujours déclenché par le <xref:System.Windows.Controls.Button> lui-même. L’événement et ses données poursuivent l’itinéraire, mais comme le <xref:System.Windows.Controls.Button> marque les données d’événement en tant que <xref:System.Windows.RoutedEventArgs.Handled%2A>, seuls les gestionnaires de l’événement qui indiquait spécifiquement qu’ils doivent agir dans le `handledEventsToo` cas sont appelées.  Si d’autres éléments vers la racine de votre application souhaitaient encore pour gérer un événement supprimé par le contrôle, une autre solution consiste à attacher des gestionnaires dans le code avec `handledEventsToo` spécifié en tant que `true`. Mais souvent une technique plus simple consiste à modifier la direction de routage que vous gérez à l’équivalent de l’aperçu d’un événement d’entrée. Par exemple, si un contrôle supprime <xref:System.Windows.UIElement.MouseLeftButtonDown>, essayez de joindre un gestionnaire pour <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> à la place. Cette technique fonctionne uniquement pour les événements d’entrée d’élément de base tels que <xref:System.Windows.UIElement.MouseLeftButtonDown>. Ces événements d’entrée utilisent des paires tunneling/propagation, déclenchent les deux événements et partagent les données d’événement.  
  
 Chacune de ces techniques a des effets secondaires ou des limitations. L’effet secondaire de gestion de l’événement d’aperçu est que gestion de l’événement à ce stade peut désactiver les gestionnaires qui s’attendent à gérer l’événement de propagation, et par conséquent, la limitation est qu’il n’est généralement pas judicieux de marquer l’événement géré alors qu’il est toujours sur le Previ partie de la nouvelle de l’itinéraire. La limitation de la `handledEventsToo` technique est que vous ne pouvez pas spécifier un `handledEventsToo` gestionnaire dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en tant qu’attribut, vous devez inscrire le Gestionnaire d’événements dans le code après avoir obtenu une référence d’objet à l’élément où le gestionnaire doit être attaché.  
  
## <a name="see-also"></a>Voir aussi  
 [Marquage des événements routés comme gérés et gestion de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
