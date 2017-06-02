---
title: "Comment&#160;: am&#233;liorer les performances d&#39;un contr&#244;le TreeView | Microsoft Docs"
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
  - "TreeView (contrôle WPF), améliorer les performances"
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: am&#233;liorer les performances d&#39;un contr&#244;le TreeView
Lorsqu'un contrôle <xref:System.Windows.Controls.TreeView> contient de nombreux éléments, la durée de son chargement risque de provoquer un ralentissement conséquent dans l'interface utilisateur.  Vous pouvez améliorer le temps de chargement en affectant à la propriété jointe <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> la valeur `true`.  L'interface utilisateur peut également être lente à réagir lorsqu'un utilisateur fait défiler le contrôle <xref:System.Windows.Controls.TreeView> à l'aide de la roulette de la souris ou en faisant glisser le curseur d'une barre de défilement.  Vous pouvez améliorer les performances de <xref:System.Windows.Controls.TreeView> lorsque l'utilisateur effectue un défilement en affectant à la propriété jointe <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> la valeur <xref:System.Windows.Controls.VirtualizationMode>.  
  
## Exemple  
  
## Description  
 L'exemple suivant crée un contrôle <xref:System.Windows.Controls.TreeView> qui affecte à <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> la valeur true et à <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> la valeur <xref:System.Windows.Controls.VirtualizationMode> pour optimiser ses performances.  
  
## Code  
 [!code-xml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 L'exemple suivant présente les données utilisées dans l'exemple précédent.  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## Voir aussi  
 [Contrôles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)