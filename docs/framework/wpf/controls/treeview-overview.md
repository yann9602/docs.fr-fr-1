---
title: Vue d'ensemble de TreeView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bf50346cc179a5aae860a7651d28e104bac3c2ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="treeview-overview"></a>Vue d'ensemble de TreeView
Le <xref:System.Windows.Controls.TreeView> contrôle fournit un moyen d’afficher des informations dans une structure hiérarchique à l’aide de nœuds réductibles. Cette rubrique présente la <xref:System.Windows.Controls.TreeView> et <xref:System.Windows.Controls.TreeViewItem> contrôle et fournit des exemples simples de leur utilisation.  
  
  
<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>Qu’est-ce qu’un contrôle TreeView ?  
 <xref:System.Windows.Controls.TreeView>est un <xref:System.Windows.Controls.ItemsControl> qui imbrique les éléments à l’aide de <xref:System.Windows.Controls.TreeViewItem> contrôles. L’exemple suivant crée un <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>Création d’un contrôle TreeView  
 Le <xref:System.Windows.Controls.TreeView> contrôle contient une hiérarchie de <xref:System.Windows.Controls.TreeViewItem> contrôles. A <xref:System.Windows.Controls.TreeViewItem> contrôle est un <xref:System.Windows.Controls.HeaderedItemsControl> qui a un <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> et un <xref:System.Windows.Controls.ItemsControl.Items%2A> collection.  
  
 Si vous définissez un <xref:System.Windows.Controls.TreeView> à l’aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez définir explicitement le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> contenu d’un <xref:System.Windows.Controls.TreeViewItem> contrôle et les éléments qui composent sa collection. L’illustration précédente montre cette méthode.  
  
 Vous pouvez également spécifier un <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> sous forme de données source, puis spécifiez un <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> et <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pour définir le <xref:System.Windows.Controls.TreeViewItem> contenu.  
  
 Pour définir la disposition d’un <xref:System.Windows.Controls.TreeViewItem> (contrôle), vous pouvez également utiliser <xref:System.Windows.HierarchicalDataTemplate> objets. Pour plus d’informations illustrées par un exemple, consultez la page [Utiliser SelectedValue, SelectedValuePath et SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Si un élément n’est pas un <xref:System.Windows.Controls.TreeViewItem> (contrôle), il est automatiquement entouré par un <xref:System.Windows.Controls.TreeViewItem> contrôle lorsque le <xref:System.Windows.Controls.TreeView> contrôle s’affiche.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Développer et réduire un élément TreeViewItem  
 Si l’utilisateur développe un <xref:System.Windows.Controls.TreeViewItem>, le <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> est définie sur `true`. Vous pouvez également développer ou réduire un <xref:System.Windows.Controls.TreeViewItem> sans intervention directe de l’utilisateur en définissant le <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> propriété `true` (développer) ou `false` (réduit). Lorsque cette propriété change, un <xref:System.Windows.Controls.TreeViewItem.Expanded> ou <xref:System.Windows.Controls.TreeViewItem.Collapsed> événement se produit.  
  
 Lorsque le <xref:System.Windows.FrameworkElement.BringIntoView%2A> méthode est appelée sur une <xref:System.Windows.Controls.TreeViewItem> (contrôle), le <xref:System.Windows.Controls.TreeViewItem> et son parent <xref:System.Windows.Controls.TreeViewItem> développer des contrôles. Si un <xref:System.Windows.Controls.TreeViewItem> n’est pas visible ou partiellement visible, le <xref:System.Windows.Controls.TreeView> fait défiler pour le rendre visible.  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>Sélection d’un élément TreeViewItem  
 Lorsqu’un utilisateur clique sur un <xref:System.Windows.Controls.TreeViewItem> contrôle pour le sélectionner, le <xref:System.Windows.Controls.TreeViewItem.Selected> événement se produit et son <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> est définie sur `true`. Le <xref:System.Windows.Controls.TreeViewItem> devient également le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> de la <xref:System.Windows.Controls.TreeView> contrôle. Inversement, lorsque la sélection change d’un <xref:System.Windows.Controls.TreeViewItem> contrôle, son <xref:System.Windows.Controls.TreeViewItem.Unselected> événement se produit et son <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> est définie sur `false`.  
  
 Le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété sur le <xref:System.Windows.Controls.TreeView> contrôle est une propriété en lecture seule ; par conséquent, vous ne pouvez pas définir explicitement. Le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété est définie si l’utilisateur clique sur un <xref:System.Windows.Controls.TreeViewItem> contrôle ou lorsque le <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> est définie sur `true` sur la <xref:System.Windows.Controls.TreeViewItem> contrôle.  
  
 Utilisez le <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété pour spécifier un <xref:System.Windows.Controls.TreeView.SelectedValue%2A> d’un <xref:System.Windows.Controls.TreeView.SelectedItem%2A>. Pour plus d’informations, consultez la page [Utiliser SelectedValue, SelectedValuePath et SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Vous pouvez inscrire un gestionnaire d’événements sur le <xref:System.Windows.Controls.TreeView.SelectedItemChanged> événement afin de déterminer quand un <xref:System.Windows.Controls.TreeViewItem> modifications. Le <xref:System.Windows.RoutedPropertyChangedEventArgs%601> qui est fourni à l’événement gestionnaire spécifie le <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>, qui est la sélection précédente et le <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, qui est la sélection actuelle. Les deux valeurs peuvent être `null` si l’application ou l’utilisateur n’a effectué aucune sélection (aussi bien une sélection précédente qu’une sélection en cours).  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>Style de TreeView  
 Le style par défaut pour un <xref:System.Windows.Controls.TreeView> contrôle place à l’intérieur d’un <xref:System.Windows.Controls.StackPanel> objet qui contient un <xref:System.Windows.Controls.ScrollViewer> contrôle. Lorsque vous définissez la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés pour un <xref:System.Windows.Controls.TreeView>, ces valeurs sont utilisées pour la taille de la <xref:System.Windows.Controls.StackPanel> objet qui affiche le <xref:System.Windows.Controls.TreeView>. Si le contenu à afficher est supérieur à la zone d’affichage, un <xref:System.Windows.Controls.ScrollViewer> affiche automatiquement afin que l’utilisateur peut faire défiler le <xref:System.Windows.Controls.TreeView> contenu.  
  
 Pour personnaliser l’apparence d’un <xref:System.Windows.Controls.TreeViewItem> , affectez la <xref:System.Windows.FrameworkElement.Style%2A> propriété personnalisée <xref:System.Windows.Style>.  
  
 L’exemple suivant montre comment définir la <xref:System.Windows.Controls.Control.Foreground%2A> et <xref:System.Windows.Controls.Control.FontSize%2A> valeurs des propriétés d’un <xref:System.Windows.Controls.TreeViewItem> contrôle en utilisant un <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xaml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>Ajouter des images et d’autres contenus à des éléments TreeView  
 Vous pouvez inclure plusieurs objets dans le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> contenu d’un <xref:System.Windows.Controls.TreeViewItem>. Pour inclure plusieurs objets dans <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> de contenu, placez-le entre les objets à l’intérieur d’un contrôle de disposition, comme un <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.StackPanel>.  
  
 L’exemple suivant montre comment définir la <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> d’un <xref:System.Windows.Controls.TreeViewItem> comme un <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.TextBlock> que sont placés entre un <xref:System.Windows.Controls.DockPanel> contrôle.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 L’exemple suivant montre comment définir un <xref:System.Windows.DataTemplate> qui contient un <xref:System.Windows.Controls.Image> et un <xref:System.Windows.Controls.TextBlock> délimitées par un <xref:System.Windows.Controls.DockPanel> contrôle. Vous pouvez utiliser un <xref:System.Windows.DataTemplate> pour définir le <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> ou <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pour un <xref:System.Windows.Controls.TreeViewItem>.  
  
 [!code-xaml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)  
 [Modèle de contenu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md)
