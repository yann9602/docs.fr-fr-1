---
title: "Comment : ajouter des info-bulles à des cellules dans un contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a533f4cbf5000489e774ba8661c3ab03cea4948a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Comment : ajouter des info-bulles à des cellules dans un contrôle DataGridView Windows Forms
Par défaut, les info-bulles sont utilisés pour afficher les valeurs de <xref:System.Windows.Forms.DataGridView> cellules qui sont trop petits pour afficher leur contenu entier. Vous pouvez substituer ce comportement, toutefois, pour définir des valeurs de texte d’info-bulle pour les cellules individuelles. Cela est utile à afficher aux utilisateurs plus d’informations sur une cellule ou pour fournir aux utilisateurs une autre description du contenu de la cellule. Par exemple, si vous avez une ligne qui affiche des icônes d’état, vous souhaiterez fournir des explications de texte à l’aide des info-bulles.  
  
 Vous pouvez également désactiver l’affichage des info-bulles au niveau des cellules en définissant le <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> propriété `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Pour ajouter une info-bulle à une cellule  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Cet exemple nécessite :  
  
-   A <xref:System.Windows.Forms.DataGridView> contrôle nommé `dataGridView1` qui contient une colonne nommée `Rating` pour afficher des valeurs de chaîne d’un à quatre astérisque (« * ») les symboles. Le <xref:System.Windows.Forms.DataGridView.CellFormatting> événement du contrôle doit être associé à la méthode de gestionnaire d’événements indiquée dans l’exemple.  
  
-   des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Lorsque vous liez le <xref:System.Windows.Forms.DataGridView> le contrôle à une source de données externe ou fournissez votre propre source de données en implémentant le mode virtuel, vous pouvez rencontrer des problèmes de performances. Pour éviter une altération des performances lorsque vous travaillez avec grandes quantités de données, gérez le <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> événements au lieu de définir la <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriété de plusieurs cellules. Lorsque vous gérez cet événement, l’obtention de la valeur d’une cellule <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriété déclenche l’événement et retourne la valeur de la <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> de la propriété spécifié dans l’événement de gestionnaire.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
