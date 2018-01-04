---
title: "Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms"
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
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a8571209ea0a80a64c1f30336c9a52b1bc79622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b2648-102">Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2648-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b2648-103">Dans la <xref:System.Windows.Forms.DataGridView> utilisent des colonnes de zone de texte (contrôle), le tri automatique par défaut, tandis que d’autres types de colonne ne sont pas triées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b2648-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="b2648-104">Parfois, vous devez remplacer ces valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="b2648-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="b2648-105">Par exemple, vous pouvez afficher des images à la place de texte, des nombres ou des valeurs de cellule d’énumération.</span><span class="sxs-lookup"><span data-stu-id="b2648-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="b2648-106">Alors que les images ne peuvent pas être triées, les valeurs sous-jacentes qu’ils représentent peuvent être triées.</span><span class="sxs-lookup"><span data-stu-id="b2648-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="b2648-107">Dans le <xref:System.Windows.Forms.DataGridView> (contrôle), le <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> valeur de la propriété d’une colonne détermine son comportement de tri.</span><span class="sxs-lookup"><span data-stu-id="b2648-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="b2648-108">La procédure suivante affiche le `Priority` colonne à partir de [Comment : personnaliser la mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b2648-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="b2648-109">Cette colonne est une colonne d’image et n’est pas triable par défaut.</span><span class="sxs-lookup"><span data-stu-id="b2648-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="b2648-110">Il contient des valeurs de cellule réelle qui sont des chaînes, toutefois, afin qu’il peut être triée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b2648-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="b2648-111">Pour définir le mode de tri pour une colonne</span><span class="sxs-lookup"><span data-stu-id="b2648-111">To set the sort mode for a column</span></span>  
  
-   <span data-ttu-id="b2648-112">Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b2648-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2648-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b2648-113">Compiling the Code</span></span>  
 <span data-ttu-id="b2648-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b2648-114">This example requires:</span></span>  
  
-   <span data-ttu-id="b2648-115">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `Priority` ;</span><span class="sxs-lookup"><span data-stu-id="b2648-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
-   <span data-ttu-id="b2648-116">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b2648-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2648-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2648-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="b2648-118">Tri des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2648-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b2648-119">Modes de tri des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2648-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b2648-120">Guide pratique pour personnaliser le tri dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2648-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
