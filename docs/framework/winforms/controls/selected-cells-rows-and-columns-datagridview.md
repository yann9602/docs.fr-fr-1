---
title: "Comment : obtenir les cellules, lignes et colonnes sélectionnées dans le contrôle DataGridView Windows Forms"
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
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aada475af0ccac03dfa6ef9248b0fb07fd86b3ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7be70-102">Comment : obtenir les cellules, lignes et colonnes sélectionnées dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7be70-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7be70-103">Vous pouvez obtenir les cellules sélectionnées, les lignes ou les colonnes d’une <xref:System.Windows.Forms.DataGridView> contrôle en utilisant les propriétés correspondantes : <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, et <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="7be70-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="7be70-104">Dans les procédures suivantes, vous allez obtenir les cellules sélectionnées et afficher leurs index de ligne et de colonne dans un <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="7be70-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="7be70-105">Pour obtenir les cellules sélectionnées dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="7be70-105">To get the selected cells in a DataGridView control</span></span>  
  
-   <span data-ttu-id="7be70-106">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>.</span><span class="sxs-lookup"><span data-stu-id="7be70-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7be70-107">Utilisez la <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> méthode pour éviter d’afficher un nombre potentiellement important de cellules.</span><span class="sxs-lookup"><span data-stu-id="7be70-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="7be70-108">Pour obtenir les lignes sélectionnées dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="7be70-108">To get the selected rows in a DataGridView control</span></span>  
  
-   <span data-ttu-id="7be70-109">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="7be70-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="7be70-110">Pour permettre aux utilisateurs de sélectionner des lignes, vous devez définir le <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> propriété <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="7be70-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="7be70-111">Pour obtenir les colonnes sélectionnées dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="7be70-111">To get the selected columns in a DataGridView control</span></span>  
  
-   <span data-ttu-id="7be70-112">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="7be70-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="7be70-113">Pour permettre aux utilisateurs de sélectionner des colonnes, vous devez définir le <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> propriété <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="7be70-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7be70-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="7be70-114">Compiling the Code</span></span>  
 <span data-ttu-id="7be70-115">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="7be70-115">This example requires:</span></span>  
  
-   <span data-ttu-id="7be70-116"><xref:System.Windows.Forms.Button>contrôles nommés `selectedCellsButton`, `selectedRowsButton`, et `selectedColumnsButton`, chacun avec les gestionnaires pour les <xref:System.Windows.Forms.Control.Click> événement attaché.</span><span class="sxs-lookup"><span data-stu-id="7be70-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
-   <span data-ttu-id="7be70-117">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="7be70-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="7be70-118">des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Text?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7be70-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7be70-119">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="7be70-119">Robust Programming</span></span>  
 <span data-ttu-id="7be70-120">Les collections décrites dans cette rubrique n’effectuent pas efficacement lorsque un grand nombre de cellules, lignes ou colonnes est sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="7be70-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="7be70-121">Pour plus d’informations sur l’utilisation de ces collections avec de grandes quantités de données, consultez [meilleures pratiques pour la mise à l’échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7be70-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be70-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7be70-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>  
 [<span data-ttu-id="7be70-123">Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7be70-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
