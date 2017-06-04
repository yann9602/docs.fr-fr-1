---
title: "Comment&#160;: utiliser SelectedValue, SelectedValuePath et SelectedItem | Microsoft Docs"
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
  - "Control (classe), propriétés SelectedItem"
  - "Control (classe), propriétés SelectedValue"
  - "Control (classe), propriétés SelectedValuePath"
  - "Control (classe), propriétés TreeView"
  - "SelectedValue, propriétés SelectedItem"
  - "SelectedValue, propriétés SelectedValuePath"
  - "TreeView (contrôle), propriétés SelectedItem"
  - "TreeView (contrôle), propriétés SelectedValue"
  - "TreeView (contrôle), propriétés SelectedValuePath"
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: utiliser SelectedValue, SelectedValuePath et SelectedItem
Cet exemple indique comment utiliser les <xref:System.Windows.Controls.TreeView.SelectedValue%2A> et les propriétés <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> pour spécifier une valeur pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> d'un <xref:System.Windows.Controls.TreeView>.  
  
## Exemple  
 La propriété <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> fournit un moyen d'indiquer un <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> dans un <xref:System.Windows.Controls.TreeView>.  Le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> représente un objet dans la collection <xref:System.Windows.Controls.ItemsControl.Items%2A> et le <xref:System.Windows.Controls.TreeView> affiche la valeur d'une propriété unique de l'élément sélectionné.  La propriété <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> spécifie le chemin d'accès de la propriété utilisée pour déterminer la valeur de la propriété <xref:System.Windows.Controls.TreeView.SelectedValue%2A>.  Les exemples de cette rubrique illustrent ce concept.  
  
 L'exemple suivant affiche un <xref:System.Windows.Data.XmlDataProvider> qui contient des informations sur l'employé.  
  
 [!code-xml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 L'exemple suivant définit un <xref:System.Windows.HierarchicalDataTemplate> qui affiche le `EmployeeName` et `EmployeeWorkDay` de `Employee`.  Notez que le <xref:System.Windows.HierarchicalDataTemplate> ne spécifie pas le `EmployeeNumber` dans le cadre du modèle.  
  
 [!code-xml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 L'exemple suivant affiche un <xref:System.Windows.Controls.TreeView> qui utilise le <xref:System.Windows.HierarchicalDataTemplate> défini précédemment et qui définit la propriété <xref:System.Windows.Controls.TreeView.SelectedValue%2A> sur le `EmployeeNumber`.  Lorsque vous sélectionnez un `EmployeeName` dans le <xref:System.Windows.Controls.TreeView>, la propriété <xref:System.Windows.Controls.TreeView.SelectedItem%2A> retourne l'élément de données de `EmployeeInfo` qui correspond au `EmployeeName` sélectionné.  Toutefois, étant donné que <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> de ce <xref:System.Windows.Controls.TreeView> a la valeur `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> a la valeur `EmployeeNumber`.  
  
 [!code-xml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.TreeView>   
 <xref:System.Windows.Controls.TreeViewItem>   
 [Vue d'ensemble de TreeView](../../../../docs/framework/wpf/controls/treeview-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)