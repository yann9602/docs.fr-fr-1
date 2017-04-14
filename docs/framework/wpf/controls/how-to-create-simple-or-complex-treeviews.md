---
title: "Comment&#160;: cr&#233;er des arborescences simples ou complexes | Microsoft Docs"
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
  - "Control (classe), TreeView, créer"
  - "TreeView (contrôle), créer"
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: cr&#233;er des arborescences simples ou complexes
Cet exemple montre comment créer des contrôles <xref:System.Windows.Controls.TreeView> simples ou complexes.  
  
 Un <xref:System.Windows.Controls.TreeView> se compose d'une hiérarchie de contrôles <xref:System.Windows.Controls.TreeViewItem> qui peuvent contenir des chaînes de texte simples ainsi qu'un contenu plus complexe, tel que des contrôles <xref:System.Windows.Controls.Button> ou un <xref:System.Windows.Controls.StackPanel> avec contenu incorporé.  Vous pouvez définir explicitement le contenu <xref:System.Windows.Controls.TreeView> ou une source de données peut fournir le contenu.  Cette rubrique fournit des exemples de ces concepts.  
  
## Exemple  
 La propriété <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> du <xref:System.Windows.Controls.TreeViewItem> contient le contenu que le <xref:System.Windows.Controls.TreeView> affiche pour cet élément.  Un <xref:System.Windows.Controls.TreeViewItem> peut également disposer de contrôles <xref:System.Windows.Controls.TreeViewItem> comme éléments enfants et vous pouvez définir ces derniers en utilisant la propriété <xref:System.Windows.Controls.ItemsControl.Items%2A>.  
  
 L'exemple suivant montre comment définir explicitement le contenu <xref:System.Windows.Controls.TreeViewItem> en affectant une chaîne de texte à la propriété <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>.  
  
 [!code-xml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 L'exemple suivant montre comment définir les éléments enfants d'un <xref:System.Windows.Controls.TreeViewItem> en définissant les <xref:System.Windows.Controls.ItemsControl.Items%2A> qui sont des contrôles <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 L'exemple suivant montre comment créer un <xref:System.Windows.Controls.TreeView> où un <xref:System.Windows.Data.XmlDataProvider> fournit le contenu <xref:System.Windows.Controls.TreeViewItem> et un <xref:System.Windows.HierarchicalDataTemplate> définit l'apparence du contenu.  
  
 [!code-xml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 L'exemple suivant montre comment créer un <xref:System.Windows.Controls.TreeView> où le contenu <xref:System.Windows.Controls.TreeViewItem> contient des contrôles <xref:System.Windows.Controls.DockPanel> avec contenu incorporé.  
  
 [!code-xml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.TreeView>   
 <xref:System.Windows.Controls.TreeViewItem>   
 [Vue d'ensemble de TreeView](../../../../docs/framework/wpf/controls/treeview-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)