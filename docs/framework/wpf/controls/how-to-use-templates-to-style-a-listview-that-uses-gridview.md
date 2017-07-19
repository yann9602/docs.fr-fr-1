---
title: "Comment&#160;: utiliser des mod&#232;les pour appliquer un style &#224; un ListView utilisant GridView | Microsoft Docs"
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
  - "contrôles ListView, appliquer un style"
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: utiliser des mod&#232;les pour appliquer un style &#224; un ListView utilisant GridView
Cet exemple indique comment utiliser les objets <xref:System.Windows.DataTemplate> et <xref:System.Windows.Style> pour spécifier l'apparence d'un contrôle <xref:System.Windows.Controls.ListView> qui utilise un mode d'affichage <xref:System.Windows.Controls.GridView>.  
  
## Exemple  
 Les exemples suivants montrent des objets <xref:System.Windows.Style> et <xref:System.Windows.DataTemplate> qui personnalisent l'apparence d'un en\-tête de colonne pour une <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 L'exemple suivant indique comment utiliser ces objets <xref:System.Windows.Style> et <xref:System.Windows.DataTemplate> pour définir les propriétés <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> et <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> d'une <xref:System.Windows.Controls.GridViewColumn>.  La propriété <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> définit le contenu des cellules d'une colonne.  
  
 [!code-xml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 Le <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> et le <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> ne sont que deux des nombreuses propriétés que vous pouvez utiliser pour personnaliser l'apparence d'un en\-tête de colonne pour un contrôle <xref:System.Windows.Controls.GridView>.  Pour plus d'informations, consultez [Vue d'ensemble des modèles et styles d'en\-tête de colonne GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
 L'exemple suivant indique comment définir un <xref:System.Windows.DataTemplate> qui personnalise l'apparence des cellules d'une <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 L'exemple suivant indique comment utiliser ce <xref:System.Windows.DataTemplate> pour définir le contenu d'une cellule <xref:System.Windows.Controls.GridViewColumn>.  Ce modèle est utilisé à la place de la propriété <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, montrée dans l'exemple <xref:System.Windows.Controls.GridViewColumn> précédent.  
  
 [!code-xml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [Vue d'ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [Vue d'ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)