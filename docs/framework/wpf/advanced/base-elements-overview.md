---
title: "Vue d&#39;ensemble des &#233;l&#233;ments de base | Microsoft Docs"
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
  - "éléments de base"
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Vue d&#39;ensemble des &#233;l&#233;ments de base
Un pourcentage élevé de classes dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est dérivé de quatre classes souvent appelées classes d'éléments de base dans la documentation du [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)].  Ces classes sont <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement> et <xref:System.Windows.FrameworkContentElement>.  La classe <xref:System.Windows.DependencyObject> est également liée, car qu'il s'agit d'une classe de base commune à <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement>  
  
   
  
<a name="base_apis"></a>   
## API d'élément de base dans les classes WPF  
 <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement> sont dérivés de <xref:System.Windows.DependencyObject>, par le biais de voies de communication quelque peu différentes.  La différence à ce niveau s'explique en termes d'utilisation de <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> dans une interface utilisateur et de leur utilité dans une application.  <xref:System.Windows.UIElement> a également <xref:System.Windows.Media.Visual> dans sa hiérarchie de classes, qui est une classe qui expose la prise en charge de graphiques de niveau inférieur sous\-jacente à [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  <xref:System.Windows.Media.Visual> fournit une infrastructure de rendu en définissant des régions d'écran rectangulaires indépendantes.  Dans la pratique, <xref:System.Windows.UIElement> est destiné aux éléments qui prendront en charge un plus modèle d'objet plus important, qui sont sensés être rendus et mis en forme dans des régions pouvant être décrites en tant que régions d'écran rectangulaires, et dans lesquels le modèle de contenu est délibérément plus ouvert pour permettre différentes combinaisons d'éléments.  <xref:System.Windows.ContentElement> ne dérive pas de <xref:System.Windows.Media.Visual> ; selon son modèle, un <xref:System.Windows.ContentElement> doit être consommé par autre chose, tel qu'un lecteur ou une visionneuse qui interprète ensuite les éléments et produit le <xref:System.Windows.Media.Visual> complet pour que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] puisse le consommer.  Certaines classes <xref:System.Windows.UIElement> sont prévues pour être des hôtes de contenu : elles assurent l'hébergement et le rendu d'une ou plusieurs classes <xref:System.Windows.ContentElement> \(<xref:System.Windows.Controls.DocumentViewer> est un exemple d'une telle classe\).  <xref:System.Windows.ContentElement> est utilisé comme classe de base pour les éléments utilisant des modèles d'objets un peu plus petits et qui gèrent plutôt le texte, les informations ou le contenu documentaire qui peuvent être hébergés dans un <xref:System.Windows.UIElement>.  
  
### Niveau d'infrastructure et niveau principal  
 <xref:System.Windows.UIElement> sert de classe de base pour <xref:System.Windows.FrameworkElement> et <xref:System.Windows.ContentElement> sert de classe de base pour <xref:System.Windows.FrameworkContentElement>.  La raison pour ce niveau suivant de classes est de prendre en charge un [niveau principal WPF](GTMT) qui est distinct d'un [niveau d'infrastructure WPF](GTMT), cette division existant aussi dans la manière dont les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] sont répartis entre les assemblys PresentationCore et PresentationFramework.  Le niveau d'[infrastructure WPF](GTMT) représente une solution plus complète pour les besoins d'application de base, y compris l'implémentation du gestionnaire de présentation pour les présentations.  Le [niveau principal WPF](GTMT) offre un moyen d'utiliser la plupart de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sans utiliser la charge mémoire de l'assembly supplémentaire.  La distinction entre ces niveaux est très rarement importante pour la plupart des scénarios de développement d'applications standard et, en général, il est conseillé de considérer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] dans son ensemble et de ne pas vous soucier de la différence entre le [niveau d'infrastructure WPF](GTMT) et le [niveau principal WPF](GTMT).  Vous devez pouvoir être renseigné sur les distinctions de niveau si votre conception d'applications choisit de remplacer de nombreuses fonctionnalités [au niveau infrastructure WPF](GTMT), par exemple si votre solution globale possède déjà ses propres implémentations de composition [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] et de mise en page.  
  
<a name="subclassing_elements"></a>   
## Choisir de quel élément dériver  
 La méthode la plus pratique pour créer une classe personnalisée qui étend [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à dériver de l'une des classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] où vous récupérez le plus de fonctionnalités possibles que vous désirez par le biais de la hiérarchie de classes existante.  Cette section répertorie les fonctionnalités qui sont fournies avec trois des plus importantes classes d'élément pour vous aider à décider de quelle classe hériter.  
  
 Si vous implémentez un contrôle, ce qui est souvent l'une des principales raisons pour dériver d'une classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous souhaitez probablement dériver d'une classe qui soit un contrôle pratique, une classe de base de famille de contrôle, ou au moins de la classe de base <xref:System.Windows.Controls.Control>.  Pour obtenir de l'aide et des exemples pratiques, consultez [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Si vous ne créez pas de contrôle mais que vous avez besoin de dériver d'une classe plus haute dans la hiérarchie, les sections suivantes sont prévues pour vous servir de guide des caractéristiques définies dans chaque classe d'élément de base.  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.DependencyObject>, vous héritez des fonctionnalités suivantes :  
  
-   Prise en charge de <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>, et prise en charge du système de propriétés général.  
  
-   Capacité d'utiliser les propriétés de dépendance [](GTMT) et les propriétés attachées [](GTMT) implémentées comme propriétés de dépendance [](GTMT).  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.UIElement>, vous héritez de la fonctionnalité suivante en plus de celle fournie par <xref:System.Windows.DependencyObject> :  
  
-   Support de base pour les valeurs de propriété animées.  Pour plus d'informations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Support d'événement d'entrée de base et support de commandes.  Pour plus d'informations, consultez [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md) et [Vue d'ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
-   Méthodes virtuelles qui peuvent être substituées pour fournir des informations à un système de disposition.  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.FrameworkElement>, vous héritez de la fonctionnalité suivante en plus de celle fournie par <xref:System.Windows.UIElement> :  
  
-   Prise en charge des styles et des tables de montage séquentiel.  Pour plus d'informations, consultez <xref:System.Windows.Style> et [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
-   Prise en charge de la liaison de données.  Pour plus d'informations, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Prise en charge des références de ressource dynamique.  Pour plus d'informations, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Prise en charge de l'héritage de la valeur de propriété, et d'autres indicateurs dans les métadonnées qui aident à faire part des conditions traitant des propriétés aux services d'infrastructure tels que la liaison de données, les styles ou l'implémentation de l'infrastructure de disposition.  Pour plus d'informations, consultez [Métadonnées de propriété d'infrastructure](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   Le concept de l'arborescence logique [](GTMT).  Pour plus d'informations, consultez [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
-   Prise en charge pour l'implémentation pratique du système de disposition [au niveau de l'infrastructure WPF](GTMT), y compris une substitution <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> pouvant détecter des modifications aux propriétés qui influencent la disposition.  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.ContentElement>, vous héritez de la fonctionnalité suivante en plus de celle fournie par <xref:System.Windows.DependencyObject> :  
  
-   Prise en charge des animations.  Pour plus d'informations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Support d'événement d'entrée de base et support de commandes.  Pour plus d'informations, consultez [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md) et [Vue d'ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
 Si vous créez une classe qui dérive de <xref:System.Windows.FrameworkContentElement>, vous obtenez la fonctionnalité suivante en plus de celle fournie par <xref:System.Windows.ContentElement> :  
  
-   Prise en charge des styles et des tables de montage séquentiel.  Pour plus d'informations, consultez <xref:System.Windows.Style> et [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Prise en charge de la liaison de données.  Pour plus d'informations, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Prise en charge des références de ressource dynamique.  Pour plus d'informations, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Prise en charge de l'héritage de la valeur de propriété, et d'autres indicateurs dans les métadonnées qui aident à faire part des conditions traitant des propriétés aux services d'infrastructure tels que la liaison de données, les styles ou l'implémentation de l'infrastructure de disposition.  Pour plus d'informations, consultez [Métadonnées de propriété d'infrastructure](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   Vous n'héritez pas de l'accès aux modifications du système de disposition \(tel que <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>\).  Les implémentations du système de disposition sont uniquement disponibles sur <xref:System.Windows.FrameworkElement>.  Toutefois, vous héritez d'une substitution <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> pouvant détecter des modifications des propriétés qui influencent la disposition et les signaler aux hôtes de contenu.  
  
 Les modèles de contenu sont documentés pour diverses classes.  Le modèle de contenu pour une classe est l'un des facteurs dont vous devez tenir compte si vous souhaitez rechercher une classe appropriée à partir de laquelle dériver.  Pour plus d'informations, consultez [Modèle de contenu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## Autres classes de base  
  
### DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> fournit le support pour le modèle de thread [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et active tous les objets créés pour les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à associer à un <xref:System.Windows.Threading.Dispatcher>.  Même si vous ne dérivez pas de <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject> ou de <xref:System.Windows.Media.Visual>, vous devez envisager de dériver de <xref:System.Windows.Threading.DispatcherObject> pour obtenir la prise en charge de ce modèle de thread.  Pour plus d'informations, consultez [Modèle de thread](../../../../docs/framework/wpf/advanced/threading-model.md).  
  
### Visual  
 <xref:System.Windows.Media.Visual> implémente le concept d'un objet 2D qui requiert généralement une présentation visuelle dans une zone approximativement rectangulaire.  Le rendu réel d'un <xref:System.Windows.Media.Visual> se produit dans d'autres classes \(il n'est pas autonome\), mais la classe <xref:System.Windows.Media.Visual> fournit un type connu utilisé par les processus de rendu à différents niveaux.  <xref:System.Windows.Media.Visual> implémente le test de positionnement, mais il n'expose pas les événements qui signalent les résultats positifs du test de positionnement \(qui sont dans <xref:System.Windows.UIElement>\).  Pour plus d'informations, consultez [Programmation de la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/visual-layer-programming.md).  
  
### Freezable  
 <xref:System.Windows.Freezable> simule l'immuabilité dans un objet mutable en fournissant les moyens de générer des copies de l'objet lorsqu'un objet immuable est requis ou souhaité pour des raisons de performance.  Le type <xref:System.Windows.Freezable> fournit une base commune pour certains éléments graphiques tels que les géométries et les pinceaux, ainsi que les animations.  Particulièrement, un <xref:System.Windows.Freezable> n'est pas un <xref:System.Windows.Media.Visual>; il peut contenir des propriétés qui deviennent des sous\-propriétés lorsque le <xref:System.Windows.Freezable> est appliqué pour remplir une valeur de propriété d'un autre objet, et ces sous\-propriétés peuvent affecter le rendu.  Pour plus d'informations, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> est une classe dérivée <xref:System.Windows.Freezable> qui ajoute spécifiquement la couche de contrôle d'animation et quelques membres utilitaires afin que les propriétés actuellement animées puissent être distinguées des propriétés non animées.  
  
### Contrôle  
 <xref:System.Windows.Controls.Control> est la classe de base prévue pour le type d'objet appelé tantôt contrôle ou composant, selon la technologie.  En général, les classes de contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont des classes qui représentent directement un contrôle d'interface utilisateur ou qui participent étroitement à la composition de contrôle.  La principale fonctionnalité activée par <xref:System.Windows.Controls.Control> est la création de modèles de contrôle.  
  
## Voir aussi  
 <xref:System.Windows.Controls.Control>   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [Architecture de WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)