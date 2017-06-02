---
title: "Vue d&#39;ensemble de ListView | Microsoft Docs"
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
  - "contrôles, ListView"
  - "contrôles ListView (WPF), à propos du contrôle ListView"
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Vue d&#39;ensemble de ListView
Le contrôle <xref:System.Windows.Controls.ListView> fournit l'infrastructure pour afficher un groupe d'éléments de données dans différentes dispositions ou différents affichages.  Par exemple, il se peut qu'un utilisateur souhaite afficher des éléments de données dans une table et trier ses colonnes.  
  
   
  
<a name="WhatisaListView"></a>   
## Qu'est\-ce qu'un ListView ?  
 Le contrôle <xref:System.Windows.Controls.ListView> est un <xref:System.Windows.Controls.ItemsControl> dérivé de <xref:System.Windows.Controls.ListBox>.  En général, ses éléments sont les membres d'une collection de données et sont représentés comme des objets <xref:System.Windows.Controls.ListViewItem>.  Un <xref:System.Windows.Controls.ListViewItem> est un <xref:System.Windows.Controls.ContentControl> qui ne peut contenir qu'un seul élément enfant.  Toutefois, cet élément enfant peut être n'importe quel élément visuel.  
  
<a name="DefiningaListViewView"></a>   
## Définition d'un mode d'affichage pour un ListView  
 Pour spécifier un mode d'affichage pour le contenu d'un contrôle <xref:System.Windows.Controls.ListView>, définissez la propriété <xref:System.Windows.Controls.ListView.View%2A>.  L'un des modes d'affichage fourni par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est <xref:System.Windows.Controls.GridView>, qui affiche une collection d'éléments de données dans une table avec des colonnes personnalisables.  
  
 L'exemple suivant indique comment définir un <xref:System.Windows.Controls.GridView> pour un contrôle <xref:System.Windows.Controls.ListView> qui affiche des informations sur les employés.  
  
 [!code-xml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L'illustration suivante montre comment les données apparaissent pour l'exemple précédent.  
  
 ![Sortie de ListView avec GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.png "ListViewGridView")  
  
 Vous pouvez créer un mode d'affichage personnalisé en définissant une classe qui hérite de la classe <xref:System.Windows.Controls.ViewBase>.  La classe <xref:System.Windows.Controls.ViewBase> fournit l'infrastructure dont vous avez besoin pour créer un affichage personnalisé.  Pour plus d'informations sur la création d'un affichage personnalisé, consultez [Créer un mode d'affichage personnalisé pour un ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>   
## Liaison de données à un ListView  
 Utilisez les propriétés <xref:System.Windows.Controls.ItemsControl.Items%2A> et <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> afin de spécifier des éléments pour un contrôle <xref:System.Windows.Controls.ListView>.  L'exemple suivant définit la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> sur une collection de données appelée `EmployeeInfoDataSource`.  
  
 [!code-xml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 Dans un <xref:System.Windows.Controls.GridView>, les objets <xref:System.Windows.Controls.GridViewColumn> sont liés à des champs de données spécifiés.  L'exemple suivant lie un objet <xref:System.Windows.Controls.GridViewColumn> à un champ de données en spécifiant une <xref:System.Windows.Data.Binding> pour la propriété <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Vous pouvez également spécifier une <xref:System.Windows.Data.Binding> dans la définition d'un <xref:System.Windows.DataTemplate> que vous utilisez pour appliquer un style aux cellules d'une colonne.  Dans l'exemple suivant, le <xref:System.Windows.DataTemplate> identifié avec une <xref:System.Windows.ResourceKey> définit la <xref:System.Windows.Data.Binding> pour un <xref:System.Windows.Controls.GridViewColumn>.  Notez que cet exemple ne définit pas le <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> car cela substituerait la liaison spécifiée par <xref:System.Windows.DataTemplate>.  
  
 [!code-xml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## Application d'un style à un ListView qui implémente un GridView  
 Le contrôle <xref:System.Windows.Controls.ListView> contient des objets <xref:System.Windows.Controls.ListViewItem> qui représentent les éléments de données affichés.  Vous pouvez utiliser les propriétés suivantes pour définir le contenu et le style des éléments de données :  
  
-   Sur le contrôle <xref:System.Windows.Controls.ListView>, utilisez les propriétés <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> et <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>.  
  
-   Sur le contrôle <xref:System.Windows.Controls.ListViewItem> utilisez les propriétés <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> et <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>.  
  
 Pour éviter des problèmes d'alignement entre les cellules d'un <xref:System.Windows.Controls.GridView>, n'utilisez pas <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pour définir des propriétés ou ajouter du contenu qui affecte la largeur d'un élément dans un <xref:System.Windows.Controls.ListView>.  Par exemple, un problème d'alignement peut se produire lorsque vous définissez la propriété <xref:System.Windows.FrameworkElement.Margin%2A> dans <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>.  Pour spécifier des propriétés ou définir du contenu qui affecte la largeur des éléments dans un <xref:System.Windows.Controls.GridView>, utilisez les propriétés de la classe <xref:System.Windows.Controls.GridView> et de ses classes associées, telles que <xref:System.Windows.Controls.GridViewColumn>.  
  
 Pour plus d'informations sur la manière d'utiliser <xref:System.Windows.Controls.GridView> et ses classes prises en charge, consultez [Vue d'ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md).  
  
 Si vous définissez un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pour un contrôle <xref:System.Windows.Controls.ListView> et que vous définissez également un <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, vous devez inclure un <xref:System.Windows.Controls.ContentPresenter> dans le style afin que le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> fonctionne correctement.  
  
 N'utilisez pas les propriétés <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> et <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> pour le contenu <xref:System.Windows.Controls.ListView> affiché à l'aide d'un <xref:System.Windows.Controls.GridView>.  Pour spécifier l'alignement du contenu d'une colonne d'un <xref:System.Windows.Controls.GridView>, définissez un <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## Partage du même mode d'affichage  
 Deux contrôles <xref:System.Windows.Controls.ListView> ne peuvent pas partager le même mode d'affichage au même moment.  Si vous essayez d'utiliser le même mode d'affichage avec plus d'un contrôle <xref:System.Windows.Controls.ListView>, une exception est levée.  
  
 Pour spécifier un mode d'affichage qui peut être utilisé simultanément par plus d'un <xref:System.Windows.Controls.ListView>, utilisez des modèles ou des styles.  Pour obtenir un exemple expliquant comme définir des vues en tant que <xref:System.Windows.FrameworkElement.Resources%2A>, consultez [ListView avec plusieurs vues, exemple](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
<a name="CreatingaCustomView"></a>   
## Création d'un mode d'affichage personnalisé  
 Les affichages personnalisés tels que <xref:System.Windows.Controls.GridView> sont dérivés de la classe abstraite <xref:System.Windows.Controls.ViewBase> qui fournit les outils pour afficher des éléments de données représentés en tant qu'objets <xref:System.Windows.Controls.ListViewItem>.  
  
 Pour obtenir un exemple de mode d'affichage personnalisé, consultez [ListView avec plusieurs vues, exemple](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
## Voir aussi  
 <xref:System.Windows.Controls.GridView>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.ListViewItem>   
 <xref:System.Windows.Data.Binding>   
 [Vue d'ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [Contrôles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)