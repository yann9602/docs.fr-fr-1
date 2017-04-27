---
title: "&#201;v&#233;nements de la dur&#233;e de vie d&#39;un objet | Microsoft Docs"
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
  - "événements Activated"
  - "objets Application, événements de durée de vie"
  - "classes, Frame"
  - "classes, NavigationWindow"
  - "événements Closed"
  - "événements Closing"
  - "événements ContentRendered"
  - "événements Deactivated"
  - "événements, Activated"
  - "événements, Fermé"
  - "événements, Closing"
  - "événements, ContentRendered"
  - "événements, Deactivated"
  - "événements, Initialisé"
  - "événements, Chargé"
  - "événements, Non chargé"
  - "événements de sortie"
  - "Frame (classe)"
  - "événements Initialized"
  - "événements de durée de vie d'objets"
  - "événements Loaded"
  - "NavigationWindow (classe)"
  - "événements de durée de vie d'objets"
  - "événements de démarrage"
  - "événements Unloaded"
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# &#201;v&#233;nements de la dur&#233;e de vie d&#39;un objet
Cette rubrique décrit les événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spécifiques qui correspondent aux étapes de la durée de vie de création, d'utilisation et de destruction d'un objet.  
  
   
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous maîtrisiez les [propriétés de dépendance](GTMT) du point de vue d'un consommateur de propriétés de dépendance existantes dans les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et que vous ayez lu la rubrique [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Pour pouvoir suivre les exemples dans cette rubrique, vous devez également maîtriser le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] \(voir [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)\) et savoir écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>   
## Événements de la durée de vie d'un objet  
 Tous les objets du code managé [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] passent par des phases similaires de durée de vie, de création, d'utilisation et de destruction.  De nombreux objets ont également une étape de finalisation de vie qui se produit dans le cadre de la phase de destruction.  Les objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], plus spécifiquement les objets visuels que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identifie comme éléments, ont également un ensemble d'étapes communes de vie d'objet.  Les modèles de programmation et d'application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exposent ces phases sous la forme d'une série d'événements.  Il existe quatre types principaux d'objets dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en ce qui concerne les événements de durée de vie ; éléments en général, éléments de fenêtre, hôtes de navigation et objets d'application.  Les fenêtres et les hôtes de navigation appartiennent également au groupe plus large des objets visuels \(éléments\).  Cette rubrique décrit les événements de durée de vie communs à tous les éléments et présente les événements plus spécifiques qui s'appliquent aux définitions d'application, aux fenêtres ou aux hôtes de navigation.  
  
<a name="common_events"></a>   
## Événements de durée de vie communs des éléments  
 Tout élément de [niveau d'infrastructure WPF](GTMT) \(objets dérivés de <xref:System.Windows.FrameworkElement> ou de <xref:System.Windows.FrameworkContentElement>\) a trois événements de durée de vie communs : <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded> et <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### Initialized  
 <xref:System.Windows.FrameworkElement.Initialized> est déclenché en premier et correspond approximativement à l'initialisation de l'objet par l'appel à son constructeur.  Étant donné que l'événement est déclenché en réponse à l'initialisation, vous êtes assuré que toutes les propriétés de l'objet sont définies.  \(Il existe une exception pour les utilisations d'expressions, telles que les ressources dynamiques ou la liaison ; ces expressions ne seront pas évaluées.\) Toutes les propriétés devant être définies, la séquence de déclenchement de <xref:System.Windows.FrameworkElement.Initialized> par des éléments imbriqués définis dans le balisage a lieu à partir des éléments les plus éloignés dans l'arborescence d'éléments, puis se poursuit avec les éléments parents vers la racine.  Cet ordre s'explique par le fait que les relations parent\-enfant et contenant\-contenu sont des propriétés. Par conséquent, le parent ne peut pas signaler l'initialisation tant que les éléments enfants qui remplissent la propriété ne sont pas complètement initialisés.  
  
 Lorsque vous écrivez des gestionnaires en réponse à l'événement <xref:System.Windows.FrameworkElement.Initialized>, vous devez tenir compte du fait que tous les autres éléments de l'arborescence des éléments \([arborescence logique](GTMT) ou [arborescence d'éléments visuels](GTMT)\), près de l'emplacement où le gestionnaire est attaché, ne sont pas obligatoirement créés, notamment les éléments parents.  Les variables membres peuvent être null ou les sources de données peuvent ne pas être encore remplies par la liaison sous\-jacente \(même au niveau de l'expression\).  
  
### Loaded  
 <xref:System.Windows.FrameworkElement.Loaded> est déclenché ensuite.  L'événement <xref:System.Windows.FrameworkElement.Loaded> est déclenché avant le rendu final, mais après que le système de disposition a calculé toutes les valeurs nécessaires pour le rendu.  <xref:System.Windows.FrameworkElement.Loaded> implique que l'arborescence logique dans laquelle un élément est contenu est terminée et se connecte à une source de présentation qui fournit le HWND et la surface de rendu.  La liaison de données standard \(liaison à des sources locales, telles que d'autres propriétés ou des sources de données directement définies\) se produira avant <xref:System.Windows.FrameworkElement.Loaded>.  La liaison de données asynchrone \(sources externes ou dynamiques\) peut avoir eu lieu, mais du fait même de sa nature asynchrone elle peut ne pas avoir eu lieu.  
  
 Le mécanisme de déclenchement de l'événement <xref:System.Windows.FrameworkElement.Loaded> est différent de celui de <xref:System.Windows.FrameworkElement.Initialized>.  L'événement <xref:System.Windows.FrameworkElement.Initialized> est déclenché élément par un élément sans coordination directe par une arborescence d'éléments complétée.  En revanche, l'événement <xref:System.Windows.FrameworkElement.Loaded> est déclenché de manière coordonnée dans l'ensemble de l'arborescence d'éléments \(notamment dans l'[arborescence logique](GTMT)\).  Lorsque tous les éléments de l'arborescence ont un état les considérant comme étant chargés, l'événement <xref:System.Windows.FrameworkElement.Loaded> est déclenché en premier à la racine de l'élément.  L'événement <xref:System.Windows.FrameworkElement.Loaded> est déclenché successivement sur chaque élément enfant.  
  
> [!NOTE]
>  Ce comportement peut ressembler superficiellement au tunneling pour un [événement routé](GTMT).  Toutefois, aucune information n'est passée d'un événement vers un autre.  Chaque élément a toujours la possibilité de gérer son événement <xref:System.Windows.FrameworkElement.Loaded> et le marquage des données d'événement comme étant gérées n'a aucun effet au\-delà de l'élément.  
  
### Unloaded  
 <xref:System.Windows.FrameworkElement.Unloaded> est déclenché en dernier et il est initialisé par la source de présentation ou le parent visuel à supprimer.  Lorsque <xref:System.Windows.FrameworkElement.Unloaded> est déclenché et géré, l'élément qui correspond au parent source de l'événement \(défini par la propriété <xref:System.Windows.FrameworkElement.Parent%2A>\) ou la définition de tout élément au\-dessus dans l'arborescence logique ou visuelle peuvent avoir déjà été annulés, ce qui implique que la liaison de données, les références à une ressource et les styles peuvent ne pas être avoir leur valeur normale ou leur dernière valeur runtime connue.  
  
<a name="application_model_elements"></a>   
## Éléments de modèle d'application d'événements de durée de vie  
 Les éléments de modèle d'application suivants reposent sur les événements de durée de vie communs des éléments : <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow> et <xref:System.Windows.Controls.Frame>.  Ces éléments étendent les événements de durée de vie communs avec des événements supplémentaires en rapport avec leur fonction.  Ils sont décrits en détail dans les emplacements suivants :  
  
-   <xref:System.Windows.Application>: [Vue d'ensemble de la gestion d'applications](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [Vue d'ensemble des fenêtres WPF](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> et [Vue d'ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
## Voir aussi  
 [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)