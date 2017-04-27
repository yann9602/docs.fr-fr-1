---
title: "Vue d&#39;ensemble de TreeView | Microsoft Docs"
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
  - "Control (classe), TreeView"
  - "développer le nœud"
  - "TreeView (contrôle), à propos du contrôle TreeView"
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# Vue d&#39;ensemble de TreeView
Le contrôle <xref:System.Windows.Controls.TreeView> offre un moyen d'afficher des informations dans une structure hiérarchique en utilisant des nœuds réductibles.  Cette rubrique présente les contrôles <xref:System.Windows.Controls.TreeView> et <xref:System.Windows.Controls.TreeViewItem> et fournit des exemples simples de leur utilisation.  
  
   
  
<a name="Simple_TreeView_Control"></a>   
## Qu'est\-ce qu'un TreeView ?  
 <xref:System.Windows.Controls.TreeView> est un <xref:System.Windows.Controls.ItemsControl> qui imbrique les éléments en utilisant les contrôles <xref:System.Windows.Controls.TreeViewItem>.  L'exemple suivant crée un <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## Création d'un TreeView  
 Le contrôle <xref:System.Windows.Controls.TreeView> contient une hiérarchie de contrôles <xref:System.Windows.Controls.TreeViewItem>.  Un contrôle <xref:System.Windows.Controls.TreeViewItem> est un <xref:System.Windows.Controls.HeaderedItemsControl> qui dispose d'un <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> et d'une collection <xref:System.Windows.Controls.ItemsControl.Items%2A>.  
  
 Si vous définissez un <xref:System.Windows.Controls.TreeView> en utilisant [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez définir explicitement le contenu <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> d'un contrôle <xref:System.Windows.Controls.TreeViewItem> et les éléments qui composent sa collection.  L'illustration précédente démontre cette méthode.  
  
 Vous pouvez également spécifier un <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> comme source de données, puis spécifier un <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> et un <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pour définir le contenu <xref:System.Windows.Controls.TreeViewItem>.  
  
 Pour définir la disposition d'un contrôle <xref:System.Windows.Controls.TreeViewItem>, vous pouvez également utiliser des objets <xref:System.Windows.HierarchicalDataTemplate>.  Pour obtenir des informations supplémentaires et un exemple, consultez [Utiliser SelectedValue, SelectedValuePath et SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Si un élément n'est pas un contrôle <xref:System.Windows.Controls.TreeViewItem>, il est automatiquement entouré par un contrôle <xref:System.Windows.Controls.TreeViewItem> lorsque le contrôle <xref:System.Windows.Controls.TreeView> est affiché.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## Développement et réduction d'un TreeViewItem  
 Si l'utilisateur développe un <xref:System.Windows.Controls.TreeViewItem>, la propriété <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> a la valeur `true`.  Vous pouvez également développer ou réduire un <xref:System.Windows.Controls.TreeViewItem> sans action d'utilisateur directe, en affectant à la propriété <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> la valeur `true` \(développer\) ou `false` \(réduire\).  Lorsque cette propriété change, un évènement <xref:System.Windows.Controls.TreeViewItem.Expanded> ou <xref:System.Windows.Controls.TreeViewItem.Collapsed> se produit.  
  
 Lorsque la méthode <xref:System.Windows.FrameworkElement.BringIntoView%2A> est appelée sur un contrôle <xref:System.Windows.Controls.TreeViewItem>, le <xref:System.Windows.Controls.TreeViewItem> et ses contrôles <xref:System.Windows.Controls.TreeViewItem> parents sont développés.  Si un <xref:System.Windows.Controls.TreeViewItem> n'est pas visible ou partiellement visible, le <xref:System.Windows.Controls.TreeView> fait défiler pour le rendre visible.  
  
<a name="TreeViewItem_Selection"></a>   
## Sélection d'un TreeViewItem  
 Lorsqu'un utilisateur clique sur un contrôle <xref:System.Windows.Controls.TreeViewItem> pour le sélectionner, l'événement <xref:System.Windows.Controls.TreeViewItem.Selected> se produit et sa propriété <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> a la valeur `true`.  Le <xref:System.Windows.Controls.TreeViewItem> devient également le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> du contrôle <xref:System.Windows.Controls.TreeView>.  Inversement, lorsque la sélection change de contrôle <xref:System.Windows.Controls.TreeViewItem>, son événement <xref:System.Windows.Controls.TreeViewItem.Unselected> se produit et sa propriété <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> a la valeur `false`.  
  
 La propriété <xref:System.Windows.Controls.TreeView.SelectedItem%2A> sur le contrôle <xref:System.Windows.Controls.TreeView> est une propriété en lecture seule ; vous ne pouvez donc pas la définir explicitement.  La propriété <xref:System.Windows.Controls.TreeView.SelectedItem%2A> est définie si l'utilisateur clique sur un contrôle <xref:System.Windows.Controls.TreeViewItem> ou lorsque la propriété <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> a la valeur `true` sur le contrôle <xref:System.Windows.Controls.TreeViewItem>.  
  
 Utilisez la propriété <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> pour spécifier un <xref:System.Windows.Controls.TreeView.SelectedValue%2A> d'un <xref:System.Windows.Controls.TreeView.SelectedItem%2A>.  Pour plus d'informations, consultez [Utiliser SelectedValue, SelectedValuePath et SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Vous pouvez enregistrer un gestionnaire d'événements sur l'événement <xref:System.Windows.Controls.TreeView.SelectedItemChanged> pour déterminer à quel moment un <xref:System.Windows.Controls.TreeViewItem> sélectionné est modifié.  Le <xref:System.Windows.RoutedPropertyChangedEventArgs%601> qui est fourni au gestionnaire d'événements spécifie le <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>, qui correspond à la sélection précédente, et le <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, qui correspond à la sélection actuelle.  L'une ou l'autre de ces valeurs peut être `null` si l'application ou l'utilisateur n'a pas fait de sélection précédente ou actuelle.  
  
<a name="TreeView_Style"></a>   
## Style d'un TreeView  
 Le style par défaut pour un contrôle <xref:System.Windows.Controls.TreeView> le place à l'intérieur d'un objet <xref:System.Windows.Controls.StackPanel> qui contient un contrôle <xref:System.Windows.Controls.ScrollViewer>.  Lorsque vous définissez les propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> pour un <xref:System.Windows.Controls.TreeView>, ces valeurs sont utilisées pour dimensionner l'objet <xref:System.Windows.Controls.StackPanel> qui affiche le <xref:System.Windows.Controls.TreeView>.  Si le contenu à afficher est plus grand que la zone d'affichage, un <xref:System.Windows.Controls.ScrollViewer> s'affiche automatiquement afin que l'utilisateur puisse faire défiler le contenu <xref:System.Windows.Controls.TreeView>.  
  
 Pour personnaliser l'apparence d'un contrôle <xref:System.Windows.Controls.TreeViewItem>, affectez à la propriété <xref:System.Windows.FrameworkElement.Style%2A> un <xref:System.Windows.Style> personnalisé.  
  
 L'exemple suivant montre comment définir les valeurs des propriétés <xref:System.Windows.Controls.Control.Foreground%2A> et <xref:System.Windows.Controls.Control.FontSize%2A> pour un contrôle <xref:System.Windows.Controls.TreeViewItem> en utilisant un <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## Ajout d'images et autre contenu aux éléments TreeView  
 Vous pouvez inclure plusieurs objets dans le contenu <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> d'un <xref:System.Windows.Controls.TreeViewItem>.  Pour inclure plusieurs objets dans le contenu <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>, insérez les objets dans un contrôle de disposition, tel qu'un <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.StackPanel>.  
  
 L'exemple suivant indique comment définir le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> d'un <xref:System.Windows.Controls.TreeViewItem> comme <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.TextBlock> tous deux insérés dans un contrôle <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-xml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 L'exemple suivant indique comment définir un <xref:System.Windows.DataTemplate> qui contient un <xref:System.Windows.Controls.Image> et un <xref:System.Windows.Controls.TextBlock> qui sont insérés dans un contrôle <xref:System.Windows.Controls.DockPanel>.  Vous pouvez utiliser un <xref:System.Windows.DataTemplate> pour définir le <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> ou le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pour un <xref:System.Windows.Controls.TreeViewItem>.  
  
 [!code-xml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.TreeView>   
 <xref:System.Windows.Controls.TreeViewItem>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)   
 [Modèle de contenu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md)