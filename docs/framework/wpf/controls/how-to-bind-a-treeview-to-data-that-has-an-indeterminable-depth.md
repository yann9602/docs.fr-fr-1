---
title: "Comment : lier un TreeView à des données dont la profondeur ne peut pas être déterminée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be21ecb75420b6499e5b95d5f4d93a5f079f9646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Comment : lier un TreeView à des données dont la profondeur ne peut pas être déterminée
Il peut arriver lorsque vous souhaitez lier un <xref:System.Windows.Controls.TreeView> à une source de données dont la profondeur n’est pas connue.  Cela peut se produire lorsque les données sont récursives par nature, par exemple un système de fichiers où les dossiers peuvent contenir des dossiers, ou la structure d’organisation de l’entreprise, où les utilisateurs disposent collaborateurs directs d’autres employés.  
  
 La source de données doit avoir un modèle objet hiérarchique. Par exemple, un `Employee` classe peut contenir une collection d’objets Employee qui sont les rapports directs d’un employé. Si les données sont représentées d’une manière qui n’est pas hiérarchique, vous devez générer une représentation hiérarchique des données.  
  
 Lorsque vous définissez la <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> propriété et, si le <xref:System.Windows.Controls.ItemsControl> génère une <xref:System.Windows.Controls.ItemsControl> pour chaque élément enfant, puis l’enfant <xref:System.Windows.Controls.ItemsControl> utilise le même <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> comme parent. Par exemple, si vous définissez la <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété sur une limite de données <xref:System.Windows.Controls.TreeView>, chaque <xref:System.Windows.Controls.TreeViewItem> qui est généré utilise le <xref:System.Windows.DataTemplate> qui a été assigné à la <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété de la <xref:System.Windows.Controls.TreeView>.  
  
 Le <xref:System.Windows.HierarchicalDataTemplate> vous permet de spécifier le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour un <xref:System.Windows.Controls.TreeViewItem>, ou n’importe quel <xref:System.Windows.Controls.HeaderedItemsControl>, sur le modèle de données. Lorsque vous définissez la <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> propriété, cette valeur est utilisée lorsque la <xref:System.Windows.HierarchicalDataTemplate> est appliqué. En utilisant un <xref:System.Windows.HierarchicalDataTemplate>, vous pouvez définir de manière récursive la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour chaque <xref:System.Windows.Controls.TreeViewItem> dans le <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment lier un <xref:System.Windows.Controls.TreeView> sur les données hiérarchiques et utiliser un <xref:System.Windows.HierarchicalDataTemplate> pour spécifier le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour chaque <xref:System.Windows.Controls.TreeViewItem>.  Le <xref:System.Windows.Controls.TreeView> est liée aux données XML qui représentent les employés de l’entreprise.  Chaque `Employee` élément peut contenir d’autres `Employee` éléments pour indiquer les employés auxquels. Les données étant récursives, le <xref:System.Windows.HierarchicalDataTemplate> peuvent être appliquées à chaque niveau.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Vue d’ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md)
