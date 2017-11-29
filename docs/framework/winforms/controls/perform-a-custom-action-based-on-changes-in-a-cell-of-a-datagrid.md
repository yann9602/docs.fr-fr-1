---
title: "Comment : exécuter une action personnalisée basée sur les modifications apportées dans une cellule d'un contrôle DataGridView Windows Form"
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
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f81cf7df0272a1b90de77332712b3b8a9e202de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="59bc2-102">Comment : exécuter une action personnalisée basée sur les modifications apportées dans une cellule d'un contrôle DataGridView Windows Form</span><span class="sxs-lookup"><span data-stu-id="59bc2-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="59bc2-103">Le <xref:System.Windows.Forms.DataGridView> contrôle a un nombre d’événements que vous pouvez utiliser pour détecter des modifications dans l’état de <xref:System.Windows.Forms.DataGridView> cellules.</span><span class="sxs-lookup"><span data-stu-id="59bc2-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="59bc2-104">Parmi les plus couramment utilisés sont les <xref:System.Windows.Forms.DataGridView.CellValueChanged> et <xref:System.Windows.Forms.DataGridView.CellStateChanged> les événements.</span><span class="sxs-lookup"><span data-stu-id="59bc2-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="59bc2-105">Pour détecter des modifications dans les valeurs des cellules DataGridView</span><span class="sxs-lookup"><span data-stu-id="59bc2-105">To detect changes in the values of DataGridView cells</span></span>  
  
-   <span data-ttu-id="59bc2-106">Écrivez un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellValueChanged> événement.</span><span class="sxs-lookup"><span data-stu-id="59bc2-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="59bc2-107">Pour détecter des modifications dans les États des cellules DataGridView</span><span class="sxs-lookup"><span data-stu-id="59bc2-107">To detect changes in the states of DataGridView cells</span></span>  
  
-   <span data-ttu-id="59bc2-108">Écrivez un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellStateChanged> événement.</span><span class="sxs-lookup"><span data-stu-id="59bc2-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59bc2-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="59bc2-109">Compiling the Code</span></span>  
 <span data-ttu-id="59bc2-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="59bc2-110">This example requires:</span></span>  
  
-   <span data-ttu-id="59bc2-111">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="59bc2-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="59bc2-112">Pour c#, les gestionnaires d’événements doivent être connectés pour les événements correspondants.</span><span class="sxs-lookup"><span data-stu-id="59bc2-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
-   <span data-ttu-id="59bc2-113">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59bc2-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bc2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59bc2-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>  
 [<span data-ttu-id="59bc2-115">Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59bc2-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 [<span data-ttu-id="59bc2-116">Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59bc2-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
