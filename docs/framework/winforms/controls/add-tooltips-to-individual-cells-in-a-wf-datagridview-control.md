---
title: "Comment&#160;: ajouter des info-bulles &#224; des cellules dans un contr&#244;le DataGridView Windows&#160;Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "grilles de données, ajouter des info-bulles"
  - "DataGridView (contrôle Windows Forms), ajouter des info-bulles"
  - "info-bulles (Windows Forms), ajouter aux grilles de données"
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: ajouter des info-bulles &#224; des cellules dans un contr&#244;le DataGridView Windows&#160;Forms
Par défaut, les info\-bulles sont utilisées pour afficher les valeurs des cellules <xref:System.Windows.Forms.DataGridView> qui sont trop petites pour afficher leur contenu entier.  Toutefois, vous pouvez substituer ce comportement pour définir des valeurs ToolTip\-text pour les cellules individuelles.  Ceci est utile pour afficher aux utilisateurs des informations supplémentaires à propos d'une cellule ou pour fournir une autre description du contenu de la cellule.  Par exemple, si vous avez une ligne qui affiche des icônes d'état, vous pouvez éventuellement fournir des explications de texte à l'aide d'info\-bulles.  
  
 Vous pouvez également désactiver l'affichage des info\-bulles de niveau de la cellule en attribuant à la propriété <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=fullName> la valeur `false`.  
  
### Pour ajouter une info\-bulle à une cellule  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=fullName>.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## Compilation du code  
  
-   Cet exemple nécessite :  
  
-   Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `Rating` pour afficher des valeurs de chaîne d'un à travers quatre symboles d'astérisque \("\*"\).  L'événement <xref:System.Windows.Forms.DataGridView.CellFormatting> du contrôle doit être associé à la méthode de gestionnaire d'événements illustrée dans l'exemple.  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Programmation fiable  
 Lorsque vous liez le contrôle <xref:System.Windows.Forms.DataGridView> à une source de données externe ou fournissez votre propre source de données en implémentant le mode virtuel, vous pouvez rencontrer des problèmes de performance.  Pour éviter une altération des performances lorsque vous travaillez avec de grands volumes de données, gérez l'événement <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> au lieu de définir la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> de plusieurs cellules.  Lorsque vous gérez cet événement, l'obtention de la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> d'une cellule déclenche l'événement et retourne la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=fullName> comme spécifié dans le gestionnaire d'événements.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell>   
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=fullName>   
 [Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)