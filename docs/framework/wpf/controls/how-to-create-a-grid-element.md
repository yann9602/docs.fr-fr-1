---
title: "Comment&#160;: cr&#233;er un &#233;l&#233;ment de grille | Microsoft Docs"
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
  - "Grid (contrôle), créer, instance de grille"
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: cr&#233;er un &#233;l&#233;ment de grille
## Exemple  
 L'exemple suivant montre comment créer et utiliser une instance de <xref:System.Windows.Controls.Grid> en utilisant soit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], soit du code.  Cet exemple utilise trois objets <xref:System.Windows.Controls.ColumnDefinition> et trois objets <xref:System.Windows.Controls.RowDefinition> pour créer une grille comportant neuf cellules, comme dans une feuille de calcul.  Chaque cellule contient un élément <xref:System.Windows.Controls.TextBlock> qui représente des données et dont la rangée supérieure contient un <xref:System.Windows.Controls.TextBlock> auquel la propriété <xref:System.Windows.Controls.Grid.ColumnSpan%2A> est appliquée.  Pour afficher les limites de chaque cellule, la propriété <xref:System.Windows.Controls.Grid.ShowGridLines%2A> est activée.  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Grid>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)