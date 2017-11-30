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
ms.openlocfilehash: 73d12bb38e4929582a8317d8ab3d7b23a7d1f603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="f9a75-102">Comment : ajouter des info-bulles à des cellules dans un contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9a75-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f9a75-103">Par défaut, les info-bulles sont utilisés pour afficher les valeurs de <xref:System.Windows.Forms.DataGridView> cellules qui sont trop petits pour afficher leur contenu entier.</span><span class="sxs-lookup"><span data-stu-id="f9a75-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="f9a75-104">Vous pouvez substituer ce comportement, toutefois, pour définir des valeurs de texte d’info-bulle pour les cellules individuelles.</span><span class="sxs-lookup"><span data-stu-id="f9a75-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="f9a75-105">Cela est utile à afficher aux utilisateurs plus d’informations sur une cellule ou pour fournir aux utilisateurs une autre description du contenu de la cellule.</span><span class="sxs-lookup"><span data-stu-id="f9a75-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="f9a75-106">Par exemple, si vous avez une ligne qui affiche des icônes d’état, vous souhaiterez fournir des explications de texte à l’aide des info-bulles.</span><span class="sxs-lookup"><span data-stu-id="f9a75-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="f9a75-107">Vous pouvez également désactiver l’affichage des info-bulles au niveau des cellules en définissant le <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="f9a75-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="f9a75-108">Pour ajouter une info-bulle à une cellule</span><span class="sxs-lookup"><span data-stu-id="f9a75-108">To add a ToolTip to a cell</span></span>  
  
-   <span data-ttu-id="f9a75-109">définir la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> ;</span><span class="sxs-lookup"><span data-stu-id="f9a75-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f9a75-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f9a75-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f9a75-111">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="f9a75-111">This example requires:</span></span>  
  
-   <span data-ttu-id="f9a75-112">A <xref:System.Windows.Forms.DataGridView> contrôle nommé `dataGridView1` qui contient une colonne nommée `Rating` pour afficher des valeurs de chaîne d’un à quatre astérisque (« * ») les symboles.</span><span class="sxs-lookup"><span data-stu-id="f9a75-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("*") symbols.</span></span> <span data-ttu-id="f9a75-113">Le <xref:System.Windows.Forms.DataGridView.CellFormatting> événement du contrôle doit être associé à la méthode de gestionnaire d’événements indiquée dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="f9a75-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
-   <span data-ttu-id="f9a75-114">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9a75-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f9a75-115">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="f9a75-115">Robust Programming</span></span>  
 <span data-ttu-id="f9a75-116">Lorsque vous liez le <xref:System.Windows.Forms.DataGridView> le contrôle à une source de données externe ou fournissez votre propre source de données en implémentant le mode virtuel, vous pouvez rencontrer des problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="f9a75-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="f9a75-117">Pour éviter une altération des performances lorsque vous travaillez avec grandes quantités de données, gérez le <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> événements au lieu de définir la <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriété de plusieurs cellules.</span><span class="sxs-lookup"><span data-stu-id="f9a75-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="f9a75-118">Lorsque vous gérez cet événement, l’obtention de la valeur d’une cellule <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriété déclenche l’événement et retourne la valeur de la <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> de la propriété spécifié dans l’événement de gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="f9a75-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a75-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9a75-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f9a75-120">Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9a75-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
