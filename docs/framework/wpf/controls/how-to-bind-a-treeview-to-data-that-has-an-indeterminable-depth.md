---
title: "Comment&#160;: lier un TreeView &#224; des donn&#233;es dont la profondeur ne peut pas &#234;tre d&#233;termin&#233;e | Microsoft Docs"
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
  - "TreeView (contrôle WPF), lier à des données de profondeur indéterminée"
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: lier un TreeView &#224; des donn&#233;es dont la profondeur ne peut pas &#234;tre d&#233;termin&#233;e
Il se peut que vous souhaitiez lier un <xref:System.Windows.Controls.TreeView> à une source de données dont la profondeur n'est pas connue.  Cela peut se produire lorsque les données sont récursives par nature, comme dans un système de fichiers où les dossiers peuvent contenir des dossiers ou dans la structure organisationnelle d'une société où des employés sont subordonnés à d'autres employés.  
  
 La source de données doit posséder un modèle objet hiérarchique.  Par exemple, une classe `Employee` peut contenir une collection d'objets Employee qui sont subordonnés à un employé.  Si les données sont représentées d'une manière non hiérarchique, vous devez générer une représentation hiérarchique des données.  
  
 Lorsque vous définissez la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=fullName> et que le <xref:System.Windows.Controls.ItemsControl> génère un <xref:System.Windows.Controls.ItemsControl> pour chaque élément enfant, alors le <xref:System.Windows.Controls.ItemsControl> enfant utilise le même <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> que le parent.  Par exemple, si vous définissez la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> sur un <xref:System.Windows.Controls.TreeView> lié aux données, chaque <xref:System.Windows.Controls.TreeViewItem> qui est généré utilise le <xref:System.Windows.DataTemplate> qui a été assigné à la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> du <xref:System.Windows.Controls.TreeView>.  
  
 <xref:System.Windows.HierarchicalDataTemplate> permet de spécifier la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour un <xref:System.Windows.Controls.TreeViewItem>, ou n'importe quel <xref:System.Windows.Controls.HeaderedItemsControl>, sur le modèle de données.  Lorsque vous définissez la propriété <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=fullName>, cette valeur est utilisée lorsque le <xref:System.Windows.HierarchicalDataTemplate> est appliqué.  En utilisant un <xref:System.Windows.HierarchicalDataTemplate>, vous pouvez définir de manière récursive la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour chaque <xref:System.Windows.Controls.TreeViewItem> dans le <xref:System.Windows.Controls.TreeView>.  
  
## Exemple  
 L'exemple de code suivant montre comment lier un <xref:System.Windows.Controls.TreeView> à des données hiérarchiques et utiliser un <xref:System.Windows.HierarchicalDataTemplate> pour spécifier la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour chaque <xref:System.Windows.Controls.TreeViewItem>.  Le <xref:System.Windows.Controls.TreeView> effectue une liaison à des données XML qui représentent les employés dans une entreprise.  Chaque élément `Employee` peut contenir d'autres éléments `Employee` pour indiquer les employés subordonnés.  Les données étant récursives, le <xref:System.Windows.HierarchicalDataTemplate> peut être appliqué à chaque niveau.  
  
 [!code-xml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md)