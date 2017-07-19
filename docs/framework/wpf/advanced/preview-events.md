---
title: "Aper&#231;u des &#233;v&#233;nements | Microsoft Docs"
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
  - "événements, Aperçu"
  - "événements, supprimer"
  - "événements d'aperçu"
  - "supprimer des événements"
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Aper&#231;u des &#233;v&#233;nements
Les événements d'aperçu, également appelés événements de tunneling, sont des événements routés où l'itinéraire voyage de la racine de l'application vers l'élément qui a déclenché l'événement et est signalé comme source dans les données d'événement.  Tous les scénarios d'événement ne prennent pas en charge ou ne requièrent pas des événements d'aperçu. Cette rubrique décrit les situations où les événements d'aperçu existent, la manière dont les applications ou les composants doivent les gérer et les cas où il peut s'avérer approprié de créer des événements d'aperçu dans les composants ou les classes personnalisés.  
  
## Événements d'aperçu et entrée  
 En général, lorsque vous gérez des événements d'aperçu, veillez à marquer les événements gérés dans les données d'événement.  Lorsqu'un événement d'aperçu est géré sur tout élément autre que l'élément qui l'a déclenché \(l'élément signalé comme source dans les données d'événement\), l'élément n'a pas la possibilité de gérer l'événement qu'il a déclenché.  Il s'agit parfois du résultat désiré, en particulier si l'élément en question existe dans des relations dans la composition d'un contrôle.  
  
 Pour les événements d'entrée, plus spécifiquement, les événements d'aperçu partagent également des instances des données d'événement avec l'événement de propagation équivalent.  Si vous utilisez un gestionnaire de classe d'événement d'aperçu pour marquer l'événement d'entrée géré, le gestionnaire de la classe de l'événement d'entrée de propagation ne sera pas appelé.  Ou, si vous utilisez un gestionnaire d'instance d'événement d'aperçu pour marquer l'événement géré, les gestionnaires pour l'événement de propagation ne seront généralement pas appelés.  Les gestionnaires de classe ou gestionnaires d'instance peuvent être enregistrés ou attachés avec une option à appeler même si l'événement est marqué comme géré, mais cette technique n'est pas fréquemment utilisée.  
  
 Pour plus d'informations sur la gestion de classes et la façon dont elle est liée aux événements d'aperçu, consultez [Marquage des événements routés comme gérés et gestion de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
### Résolution des problèmes liés à la suppression d'événements par des contrôles  
 La gestion de contrôle composite d'événements d'entrée utilise fréquemment des événements d'aperçu.  Dans certains cas, l'auteur du contrôle supprime un événement issu de son contrôle, peut\-être pour remplacer un événement défini par un composant qui véhicule davantage d'informations ou implique un comportement plus spécifique.  Par exemple, un <xref:System.Windows.Controls.Button> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] supprime les événements de propagation <xref:System.Windows.UIElement.MouseLeftButtonDown> et <xref:System.Windows.UIElement.MouseLeftButtonDown> déclenchés par <xref:System.Windows.Controls.Button> ou ses éléments composites afin de capturer la souris et de déclencher un événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> toujours déclenché par <xref:System.Windows.Controls.Button> lui\-même.  L'événement et ses données poursuivent l'itinéraire, mais comme <xref:System.Windows.Controls.Button> marque les données d'événement comme étant <xref:System.Windows.RoutedEventArgs.Handled%2A>, seuls sont appelés les gestionnaires de l'événement qui indiquait spécifiquement qu'ils devaient agir dans les cas `handledEventsToo`.  Si d'autres éléments vers la racine de votre application souhaitaient encore pouvoir gérer un événement supprimé par contrôle, vous pouvez attacher des gestionnaires dans le code et affecter au paramètre `handledEventsToo` la valeur `true`.  Souvent, il suffit de modifier la direction de routage que vous gérez pour qu'elle soit l'aperçu équivalent d'un événement d'entrée.  Par exemple, si un contrôle supprime <xref:System.Windows.UIElement.MouseLeftButtonDown>, essayez plutôt d'attacher un gestionnaire pour <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>.  Cette technique fonctionne seulement pour les événements d'entrée d'élément de base, tels que <xref:System.Windows.UIElement.MouseLeftButtonDown>.  Ces événements d'entrée utilisent des paires tunneling\/propagation, déclenchent les deux événements et partagent les données d'événement.  
  
 Chacune de ces techniques a des effets secondaires ou des limitations.  L'effet secondaire de la gestion de l'événement d'aperçu réside dans le fait que la gestion de l'événement à ce stade peut désactiver des gestionnaires censés gérer l'événement de propagation. Par conséquent, la limitation est la suivante : il n'est généralement pas recommandé de marquer l'événement comme géré lorsqu'il se trouve encore sur la partie Aperçu de l'itinéraire.  La technique `handledEventsToo` présente la limitation suivante : vous ne pouvez pas spécifier un gestionnaire `handledEventsToo` en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] comme attribut, vous devez enregistrer le gestionnaire d'événements dans le code après avoir obtenu une référence d'objet à l'élément auquel le gestionnaire sera attaché.  
  
## Voir aussi  
 [Marquage des événements routés comme gérés et gestion de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)