---
title: "Vue d&#39;ensemble de ScrollViewer | Microsoft Docs"
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
  - "contrôles, ScrollViewer"
  - "ScrollViewer (contrôle), à propos du contrôle ScrollViewer"
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Vue d&#39;ensemble de ScrollViewer
Le contenu d'une interface utilisateur est souvent plus important que la zone d'affichage d'un écran d'ordinateur.  Le contrôle <xref:System.Windows.Controls.ScrollViewer> offre un moyen pratique d'activer le défilement du contenu dans les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Cette rubrique présente l'élément <xref:System.Windows.Controls.ScrollViewer> et fournit plusieurs exemples d'utilisation.  
  
 Cette rubrique contient les sections suivantes :  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [Contrôle ScrollViewer](#what_is_a_scrollviewer_element)  
  
-   [Défilement physique contredéfilement logique](#scrollviewer_physical_vs_logical)  
  
-   [Définition et utilisation d'un élément ScrollViewer](#scrollviewer_markup_syntax_and_sample)  
  
-   [Application d'un style à un ScrollViewer](#scrollviewer_styling_scrollviewer)  
  
-   [Pagination des documents](#scrollviewer_scroll_vs_paginate)  
  
-   [Related Topics](#seeAlsoToggle)  
  
<a name="what_is_a_scrollviewer_element"></a>   
## Contrôle ScrollViewer  
 Il existe deux éléments prédéfinis qui activent le défilement dans les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : <xref:System.Windows.Controls.Primitives.ScrollBar> et <xref:System.Windows.Controls.ScrollViewer>.  Le contrôle <xref:System.Windows.Controls.ScrollViewer> encapsule des éléments <xref:System.Windows.Controls.Primitives.ScrollBar> horizontaux et verticaux et un conteneur de contenu \(tel qu'un élément <xref:System.Windows.Controls.Panel>\) afin d'afficher d'autres éléments visibles dans une zone défilante.  Vous devez générer un objet personnalisé afin d'utiliser l'élément <xref:System.Windows.Controls.Primitives.ScrollBar> pour faire défiler le contenu.  Toutefois, vous pouvez utiliser l'élément <xref:System.Windows.Controls.ScrollViewer> lui\-même car c'est un contrôle composite qui encapsule les fonctionnalités <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 Le contrôle <xref:System.Windows.Controls.ScrollViewer> répond aux commandes de la souris et du clavier et définit de nombreuses méthodes qui permettent de faire défiler le contenu par incréments prédéterminés.  Vous pouvez utiliser l'événement <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> pour détecter une modification dans un état <xref:System.Windows.Controls.ScrollViewer>.  
  
 Un <xref:System.Windows.Controls.ScrollViewer> peut avoir un seul enfant, en général un élément <xref:System.Windows.Controls.Panel> qui peut héberger une collection d'éléments <xref:System.Windows.Controls.Panel.Children%2A>.  La propriété <xref:System.Windows.Controls.ContentPresenter.Content%2A> définit l'unique enfant du <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## Défilement physique contredéfilement logique  
 Le défilement physique est utilisé pour faire défiler le contenu par un incrément physique prédéterminé, généralement par une valeur indiquée en pixels.  Le défilement logique est utilisé pour passer à l'élément suivant dans l'arborescence logique.  Le défilement physique est défini par défaut pour la plupart des éléments <xref:System.Windows.Controls.Panel>.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge les deux types de défilement.  
  
#### Interface IScrollInfo  
 L'interface <xref:System.Windows.Controls.Primitives.IScrollInfo> représente la zone de défilement principale dans un contrôle <xref:System.Windows.Controls.ScrollViewer> ou un contrôle dérivé.  L'interface définit les propriétés et les méthodes de défilement qui peuvent être implémentées par les éléments <xref:System.Windows.Controls.Panel> qui requièrent le défilement par unité logique, plutôt que par incrément physique.  Le casting d'une instance de <xref:System.Windows.Controls.Primitives.IScrollInfo> en un <xref:System.Windows.Controls.Panel> dérivé, puis l'utilisation de ses méthodes de défilement permettent de passer facilement à l'unité logique suivante dans une collection enfant, plutôt que par incrément de pixels.  Par défaut, le contrôle <xref:System.Windows.Controls.ScrollViewer> prend en charge le défilement par unités physiques.  
  
 <xref:System.Windows.Controls.StackPanel> et <xref:System.Windows.Controls.VirtualizingStackPanel> implémentent <xref:System.Windows.Controls.Primitives.IScrollInfo> et prennent en charge le défilement logique en mode natif.  Pour les contrôles de disposition qui prennent en charge le défilement logique en mode natif, vous pouvez toujours effectuer un défilement physique en encapsulant l'élément hôte <xref:System.Windows.Controls.Panel> dans un <xref:System.Windows.Controls.ScrollViewer> et en affectant `false` à la propriété <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A>.  
  
 L'exemple de code suivant montre comment effectuer le cast d'une instance de <xref:System.Windows.Controls.Primitives.IScrollInfo> en un <xref:System.Windows.Controls.StackPanel> et utiliser les méthodes de défilement de contenu \(<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> et <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>\) définies par l'interface.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## Définition et utilisation d'un élément ScrollViewer  
 L'exemple suivant crée un <xref:System.Windows.Controls.ScrollViewer> dans une fenêtre contenant du texte et un rectangle.  Les éléments <xref:System.Windows.Controls.Primitives.ScrollBar> apparaissent uniquement lorsqu'ils sont nécessaires.  Lorsque vous redimensionnez la fenêtre, les éléments <xref:System.Windows.Controls.Primitives.ScrollBar> apparaissent et disparaissent, en raison des valeurs mises à jour des propriétés <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> et <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A>.  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## Application d'un style à un ScrollViewer  
 Comme tous les contrôles de Windows Presentation Foundation, il est possible d'appliquer un style à <xref:System.Windows.Controls.ScrollViewer> pour modifier le comportement de rendu par défaut du contrôle.  Pour plus d'informations sur le style des contrôles, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## Pagination des documents  
 Pour le contenu du document, une alternative au défilement consiste à choisir un conteneur de document qui prend en charge la pagination.  <xref:System.Windows.Documents.FlowDocument> convient aux documents conçus pour être hébergés dans un contrôle d'affichage, tel que <xref:System.Windows.Controls.FlowDocumentPageViewer>, qui prend en charge le contenu paginé sur plusieurs pages, supprimant ainsi le besoin de défilement.  <xref:System.Windows.Controls.DocumentViewer> fournit une solution pour la consultation de contenu <xref:System.Windows.Documents.FixedDocument>, qui utilise le défilement traditionnel pour afficher le contenu en dehors de la zone d'affichage.  
  
 Pour plus d'informations sur les formats de document et les options de présentation, consultez [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
## Voir aussi  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.Primitives.ScrollBar>   
 <xref:System.Windows.Controls.Primitives.IScrollInfo>   
 [Create a Scroll Viewer](http://msdn.microsoft.com/fr-fr/c8e46af7-b417-441b-aa30-791cbdbd43ef)   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Styles et modèles ScrollBar](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)   
 [Contrôles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)