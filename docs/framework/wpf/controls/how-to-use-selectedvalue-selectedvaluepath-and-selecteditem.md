---
title: "Comment : utiliser SelectedValue, SelectedValuePath et SelectedItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fdc478d62ca97f8f61c26fbbf1ee6c3ea8b4e189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Comment : utiliser SelectedValue, SelectedValuePath et SelectedItem
Cet exemple montre comment utiliser le <xref:System.Windows.Controls.TreeView.SelectedValue%2A> et <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriétés pour spécifier une valeur pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> d’un <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Exemple  
 Le <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété offre un moyen de spécifier un <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> dans un <xref:System.Windows.Controls.TreeView>. Le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> représente un objet dans le <xref:System.Windows.Controls.ItemsControl.Items%2A> collection et <xref:System.Windows.Controls.TreeView> affiche la valeur d’une propriété unique de l’élément sélectionné. Le <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété spécifie le chemin d’accès à la propriété qui est utilisée pour déterminer la valeur de la <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriété. Les exemples de cette rubrique illustrent ce concept.  
  
 L’exemple suivant montre un <xref:System.Windows.Data.XmlDataProvider> qui contient des informations sur les employés.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 L’exemple suivant définit un <xref:System.Windows.HierarchicalDataTemplate> qui affiche le `EmployeeName` et `EmployeeWorkDay` de la `Employee`. Notez que la <xref:System.Windows.HierarchicalDataTemplate> ne spécifie pas le `EmployeeNumber` en tant que partie du modèle.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 L’exemple suivant montre un <xref:System.Windows.Controls.TreeView> qui utilise défini précédemment <xref:System.Windows.HierarchicalDataTemplate> et qui définit les <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriété le `EmployeeNumber`. Lorsque vous sélectionnez un `EmployeeName` dans les <xref:System.Windows.Controls.TreeView>, le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété retourne le `EmployeeInfo` élément de données correspondant au `EmployeeName`. Toutefois, étant donné que la <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> de ce <xref:System.Windows.Controls.TreeView> a la valeur `EmployeeNumber`, le <xref:System.Windows.Controls.TreeView.SelectedValue%2A> a la valeur la `EmployeeNumber`.  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [Vue d'ensemble de TreeView](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
