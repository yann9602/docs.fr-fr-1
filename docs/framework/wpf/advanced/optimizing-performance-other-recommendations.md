---
title: "Optimisation des performances&#160;: autres recommandations | Microsoft Docs"
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
  - "pinceaux, performances"
  - "objets de test de positionnement (WPF)"
  - "opacité"
  - "ScrollBarVisibility (énumération)"
  - "services Terminal Server (rendu)"
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Optimisation des performances&#160;: autres recommandations
<a name="introduction"></a> Cette rubrique donne des recommandations pour améliorer les performances en plus de celles abordées par les rubriques de la section [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md).  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Opacité au niveau des pinceaux et opacité au niveau des éléments](#Opacity)  
  
-   [Navigation vers un objet](#Navigation_Objects)  
  
-   [Test de positionnement sur les grandes surfaces 3D](#Hit_Testing)  
  
-   [Événement CompositionTarget.Rendering](#CompositionTarget_Rendering_Event)  
  
-   [Évitez d'utiliser ScrollBarVisibility\=Auto](#Avoid_Using_ScrollBarVisibility)  
  
-   [Configurez le service FontCache de manière à réduire le temps de démarrage](#FontCache)  
  
<a name="Opacity"></a>   
## Opacité au niveau des pinceaux et opacité au niveau des éléments  
 Lorsque vous utilisez un <xref:System.Windows.Media.Brush> pour le <xref:System.Windows.Shapes.Shape.Fill%2A> ou le <xref:System.Windows.Shapes.Shape.Stroke%2A> d'un élément, il vaut mieux définir la valeur <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=fullName> que la propriété <xref:System.Windows.UIElement.Opacity%2A> de l'élément.  Modifier la propriété <xref:System.Windows.UIElement.Opacity%2A> d'un élément peut amener [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à créer une surface temporaire.  
  
<a name="Navigation_Objects"></a>   
## Navigation vers un objet  
 L'objet <xref:System.Windows.Navigation.NavigationWindow> est dérivé de <xref:System.Windows.Window> et l'étend avec la prise en charge de la navigation de contenu, principalement en combinant <xref:System.Windows.Navigation.NavigationService> et le journal.  Vous pouvez mettre à jour la zone cliente de <xref:System.Windows.Navigation.NavigationWindow> en spécifiant un [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] ou un objet.  L'exemple suivant montre ces deux méthodes.  
  
 [!code-csharp[Performance#PerformanceSnippet14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Chaque objet<xref:System.Windows.Navigation.NavigationWindow> possède un journal qui enregistre l'historique de navigation de l'utilisateur dans cette fenêtre.  L'un des objectifs du journal est de permettre aux utilisateurs de retracer leurs étapes.  
  
 Lorsque vous naviguez à l'aide d'un [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], le journal n'enregistre que la référence de l'[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].  Autrement dit, chaque fois que vous revisitez la page, elle est reconstruite dynamiquement, ce qui peut être long selon sa complexité.  Dans ce cas, le coût de stockage du journal est faible, mais le temps nécessaire à la reconstitution de la page est élevé.  
  
 Lorsque vous naviguez à l'aide d'un objet, le journal enregistre intégralement l'arborescence visuelle de l'objet.  Autrement dit, chaque fois que vous revisitez la page, elle réapparaît immédiatement sans avoir besoin d'être reconstruite.  Dans ce cas, le coût de stockage du journal est élevé, mais le temps nécessaire à la reconstitution de la page est faible.  
  
 Lorsque vous utilisez l'objet <xref:System.Windows.Navigation.NavigationWindow> vous ne devez pas perdre de vue l'impact de la journalisation sur les performances de votre application.  Pour plus d'informations, consultez [Vue d'ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## Test de positionnement sur les grandes surfaces 3D  
 Le test de positionnement sur les grandes surfaces 3D est une opération très coûteuse en termes de consommation processeur.  C'est particulièrement vrai lorsque la surface 3D est animée.  Désactivez le test de positionnement sur les grandes surfaces 3D s'il n'est pas indispensable.  Les objets dérivés de <xref:System.Windows.UIElement> peuvent désactiver le test de positionnement en attribuant la valeur `false` à la propriété <xref:System.Windows.UIElement.IsHitTestVisible%2A>.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## Événement CompositionTarget.Rendering  
 L'événement <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=fullName> demande à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d'effectuer une animation continue.  Si vous utilisez cet événement, détachez\-le chaque fois que possible.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## Évitez d'utiliser ScrollBarVisibility\=Auto  
 Chaque fois que possible, évitez d'utiliser la valeur <xref:System.Windows.Controls.ScrollBarVisibility?displayProperty=fullName> pour les propriétés `HorizontalScrollBarVisibility` et `VerticalScrollBarVisibility`.  Ces propriétés sont définies pour <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer> et les objets <xref:System.Windows.Controls.TextBox> ;elles sont également définies en tant que propriété attachée pour l'objet <xref:System.Windows.Controls.ListBox>.  Affectez plutôt à la propriété <xref:System.Windows.Controls.ScrollBarVisibility> la valeur <xref:System.Windows.Controls.ScrollBarVisibility>, <xref:System.Windows.Controls.ScrollBarVisibility> ou <xref:System.Windows.Controls.ScrollBarVisibility>.  
  
 La valeur <xref:System.Windows.Controls.ScrollBarVisibility> doit s'utiliser lorsque place est limitée et que les barres de défilement ne doivent apparaître que si nécessaire.  Par exemple, il peut être intéressant d'utiliser cette valeur de <xref:System.Windows.Controls.ScrollBarVisibility> avec une <xref:System.Windows.Controls.ListBox> de 30 éléments contrairement à une <xref:System.Windows.Controls.TextBox> d'une centaine de lignes.  
  
<a name="FontCache"></a>   
## Configurez le service FontCache de manière à réduire le temps de démarrage  
 Le service Cache de police de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] partage les données de police entre les différentes applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  La première application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] que vous exécutez démarre ce service s'il n'est pas déjà en cours d'exécution.  Si vous utilisez [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], vous pouvez modifier le paramétrage du service "Cache de police de [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 3.0.0.0" de "Manuel" \(valeur par défaut\) en "Automatique \(début différé\)" pour réduire le temps de démarrage initial des applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
## Voir aussi  
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Comportement d'objets](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Conseils et astuces sur les animations](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)