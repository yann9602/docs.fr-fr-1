---
title: "Comment&#160;: grouper des &#233;l&#233;ments dans un ListView impl&#233;mentant un GridView | Microsoft Docs"
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
  - "contrôles GridView, regrouper des éléments"
  - "regrouper des éléments dans des ListViews en implémentant des GridViews"
  - "contrôles ListView, regrouper des éléments à l'aide de GridViews"
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: grouper des &#233;l&#233;ments dans un ListView impl&#233;mentant un GridView
Cet exemple montre comment afficher des groupes d'éléments en mode d'affichage <xref:System.Windows.Controls.GridView> d'un contrôle <xref:System.Windows.Controls.ListView>.  
  
## Exemple  
 Pour afficher des groupes d'éléments dans un <xref:System.Windows.Controls.ListView>, définissez un <xref:System.Windows.Data.CollectionViewSource>.  L'exemple suivant présente un <xref:System.Windows.Data.CollectionViewSource> qui regroupe des éléments de données d'après la valeur du champ de données `Catalog`.  
  
 [!code-xml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 L'exemple suivant affecte à <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour le <xref:System.Windows.Controls.ListView> le <xref:System.Windows.Data.CollectionViewSource> défini par l'exemple précédent.  L'exemple définit également un <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> qui implémente un contrôle <xref:System.Windows.Controls.Expander>.  
  
 [!code-xml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [Vue d'ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [Vue d'ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)