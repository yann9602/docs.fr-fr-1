---
title: Vue d'ensemble de ScrollViewer
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
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7317bade85641d7d055facabcf7103b945609583
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="scrollviewer-overview"></a>Vue d'ensemble de ScrollViewer
Le contenu d’une interface utilisateur occupe souvent un espace plus important que la zone d’affiche d’un écran d’ordinateur. Le <xref:System.Windows.Controls.ScrollViewer> contrôle offre un moyen pratique d’activer le défilement du contenu dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications. Cette rubrique présente la <xref:System.Windows.Controls.ScrollViewer> élément et fournit plusieurs exemples d’utilisation.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>Le contrôle ScrollViewer  
 Il existe deux éléments prédéfinis qui permettent le défilement dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications : <xref:System.Windows.Controls.Primitives.ScrollBar> et <xref:System.Windows.Controls.ScrollViewer>. Le <xref:System.Windows.Controls.ScrollViewer> contrôle encapsule horizontal et vertical <xref:System.Windows.Controls.Primitives.ScrollBar> éléments et un conteneur de contenu (comme un <xref:System.Windows.Controls.Panel> élément) pour afficher d’autres éléments visibles dans une zone avec défilement. Vous devez créer un objet personnalisé afin d’utiliser le <xref:System.Windows.Controls.Primitives.ScrollBar> , élément pour les faire défiler le contenu. Toutefois, vous pouvez utiliser la <xref:System.Windows.Controls.ScrollViewer> élément par lui-même, car il s’agit d’un contrôle composite qui encapsule <xref:System.Windows.Controls.Primitives.ScrollBar> fonctionnalité.  
  
 Le <xref:System.Windows.Controls.ScrollViewer> contrôle répond aux commandes de la souris et du clavier et définit de nombreuses méthodes permettant de faire défiler le contenu par incréments prédéterminés. Vous pouvez utiliser la <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> événements pour détecter une modification dans un <xref:System.Windows.Controls.ScrollViewer> état.  
  
 A <xref:System.Windows.Controls.ScrollViewer> peut avoir un seul enfant, généralement un <xref:System.Windows.Controls.Panel> élément qui peut héberger un <xref:System.Windows.Controls.Panel.Children%2A> collection d’éléments. Le <xref:System.Windows.Controls.ContentPresenter.Content%2A> propriété définit l’unique enfant de la <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Défilement physique ou défilement logique  
 Le défilement physique est utilisé pour faire défiler le contenu selon un incrément physique prédéterminé, généralement une valeur déclarée en pixels. Le défilement logique est utilisé pour faire défiler l’écran jusqu’à l’élément suivant dans l’arborescence logique. Le défilement physique est le comportement de défilement par défaut pour la plupart des <xref:System.Windows.Controls.Panel> éléments. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge les deux types de défilement.  
  
#### <a name="the-iscrollinfo-interface"></a>L’interface IScrollInfo  
 Le <xref:System.Windows.Controls.Primitives.IScrollInfo> interface représente la zone de défilement principale dans un <xref:System.Windows.Controls.ScrollViewer> ou contrôle dérivé. L’interface définit les propriétés et méthodes qui peuvent être implémentées par défilement <xref:System.Windows.Controls.Panel> les éléments qui requièrent le défilement par unité logique, plutôt que par incrément physique. Conversion d’une instance de <xref:System.Windows.Controls.Primitives.IScrollInfo> à une dérivée <xref:System.Windows.Controls.Panel> et ensuite à l’aide de ses méthodes de défilement fournit un moyen utile pour accéder à l’unité logique suivante dans une collection d’enfants, plutôt que par incrément de pixels. Par défaut, le <xref:System.Windows.Controls.ScrollViewer> contrôle prend en charge le défilement en unités physiques.  
  
 <xref:System.Windows.Controls.StackPanel>et <xref:System.Windows.Controls.VirtualizingStackPanel> ils implémentent tous deux <xref:System.Windows.Controls.Primitives.IScrollInfo> et en mode natif prennent en charge le défilement logique. Pour les contrôles de disposition qui en mode natif prise en charge le défilement logique, vous pouvez toujours effectuer un défilement physique en encapsulant l’hôte <xref:System.Windows.Controls.Panel> élément dans une <xref:System.Windows.Controls.ScrollViewer> et en définissant le <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> propriété `false`.  
  
 L’exemple de code suivant montre comment effectuer un cast d’une instance de <xref:System.Windows.Controls.Primitives.IScrollInfo> à un <xref:System.Windows.Controls.StackPanel> et utiliser les méthodes de défilement de contenu (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> et <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) définies par l’interface.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Définition et utilisation d’un élément ScrollViewer  
 L’exemple suivant crée un <xref:System.Windows.Controls.ScrollViewer> dans une fenêtre qui contient du texte et un rectangle. <xref:System.Windows.Controls.Primitives.ScrollBar>les éléments apparaissent uniquement lorsqu’ils sont nécessaires. Lorsque vous redimensionnez la fenêtre, le <xref:System.Windows.Controls.Primitives.ScrollBar> éléments apparaissent et disparaissent, en raison de valeurs mises à jour de la <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> et <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> propriétés.  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Application d’un style à un élément ScrollViewer  
 Comme tous les contrôles dans Windows Presentation Foundation, le <xref:System.Windows.Controls.ScrollViewer> peut être un style pour modifier le comportement de rendu par défaut du contrôle. Pour plus d’informations sur l’application d’un style aux contrôles, consultez [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Pagination de documents  
 Pour le contenu de document, il est possible de choisir un conteneur de documents qui prend en charge la pagination plutôt que d’utiliser le défilement. <xref:System.Windows.Documents.FlowDocument>pour les documents qui sont conçus pour être hébergé dans un contrôle d’affichage, tel que <xref:System.Windows.Controls.FlowDocumentPageViewer>, qui prend en charge le contenu paginé sur plusieurs pages, ainsi le besoin de défilement. <xref:System.Windows.Controls.DocumentViewer>Fournit une solution pour l’affichage <xref:System.Windows.Documents.FixedDocument> contenu, qui utilise le défilement traditionnel pour afficher le contenu en dehors de la zone d’affichage.  
  
 Pour plus d’informations sur les formats et les options de présentation de documents, consultez [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [Créer une visionneuse de défilement](http://msdn.microsoft.com/library/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Styles et modèles ScrollBar](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)  
 [Contrôles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
