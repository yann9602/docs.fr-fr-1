---
title: "Comment&#160;: trouver un TreeViewItem dans un TreeView | Microsoft Docs"
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
  - "TreeView (contrôle WPF), rechercher un TreeViewItem"
  - "TreeViewItem (WPF), rechercher"
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: trouver un TreeViewItem dans un TreeView
Le contrôle <xref:System.Windows.Controls.TreeView> fournit un moyen pratique d'afficher des données hiérarchiques.  Si votre <xref:System.Windows.Controls.TreeView> est lié à une source de données, la propriété <xref:System.Windows.Controls.TreeView.SelectedItem%2A> est un moyen pratique de rapidement récupérer l'objet de données sélectionné.  Il est généralement préférable d'utiliser l'objet de données sous\-jacent, mais parfois, vous pouvez avoir besoin de modifier par programmation les <xref:System.Windows.Controls.TreeViewItem> contenant des données.  Par exemple, vous pouvez devoir développer <xref:System.Windows.Controls.TreeViewItem> par programmation, ou sélectionner un autre élément dans <xref:System.Windows.Controls.TreeView>.  
  
 Pour trouver un <xref:System.Windows.Controls.TreeViewItem> qui contient un objet de données spécifique, vous devez parcourir chaque niveau de <xref:System.Windows.Controls.TreeView>.  Les éléments contenus dans <xref:System.Windows.Controls.TreeView> peuvent également être virtualisés pour améliorer les performances.  Lorsque les éléments peuvent être virtualisés, vous devez également créer un <xref:System.Windows.Controls.TreeViewItem> pour vérifier s'il contient l'objet de données.  
  
## Exemple  
  
## Description  
 L'exemple suivant recherche un objet spécifique dans <xref:System.Windows.Controls.TreeView> et retourne le <xref:System.Windows.Controls.TreeViewItem> contenant l'objet.  L'exemple vérifie que chaque <xref:System.Windows.Controls.TreeViewItem> est instancié afin que la recherche puisse avoir lieu parmi les éléments enfants.  Cet exemple fonctionne également si <xref:System.Windows.Controls.TreeView> n'utilise pas d'éléments virtualisés.  
  
> [!NOTE]
>  L'exemple suivant fonctionne pour n'importe quel <xref:System.Windows.Controls.TreeView>, quel que soit le modèle de données sous\-jacent, et effectue la recherche dans tous les <xref:System.Windows.Controls.TreeViewItem> jusqu'à ce qu'il trouve l'objet.  Une autre technique plus performante consiste à rechercher l'objet spécifié dans le modèle de données, de noter son emplacement dans la hiérarchie de données, puis de rechercher le <xref:System.Windows.Controls.TreeViewItem> correspondant dans <xref:System.Windows.Controls.TreeView>.  Toutefois, la technique la plus performante nécessite des connaissances du modèle de données et ne peut pas être généralisée pour tous les <xref:System.Windows.Controls.TreeView>.  
  
## Code  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Le code précédent repose sur un <xref:System.Windows.Controls.VirtualizingStackPanel> personnalisé qui expose une méthode nommée `BringIntoView`.  Le code suivant définit le <xref:System.Windows.Controls.VirtualizingStackPanel> personnalisé.  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Le code XAML suivant indique comment créer un <xref:System.Windows.Controls.TreeView> qui utilise le <xref:System.Windows.Controls.VirtualizingStackPanel> personnalisé.  
  
 [!code-xml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## Voir aussi  
 [Améliorer les performances d'un contrôle TreeView](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)