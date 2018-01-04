---
title: "Comment : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms"
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
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75f8a96b77ffcd40a51cf484f50032f7f2e44309
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e7f37-102">Comment : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7f37-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e7f37-103">Interaction avec le <xref:System.Windows.Forms.DataGridView> requiert souvent que vous découvriez par programme la cellule qui est actuellement active.</span><span class="sxs-lookup"><span data-stu-id="e7f37-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="e7f37-104">Vous devez également modifier la cellule active.</span><span class="sxs-lookup"><span data-stu-id="e7f37-104">You may also need to change the current cell.</span></span> <span data-ttu-id="e7f37-105">Vous pouvez effectuer ces tâches avec la <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="e7f37-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7f37-106">Vous ne pouvez pas définir la cellule active dans une ligne ou une colonne qui a son <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="e7f37-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="e7f37-107">Selon la <xref:System.Windows.Forms.DataGridView> mode de sélection du contrôle, la modification de la cellule active peut modifier la sélection.</span><span class="sxs-lookup"><span data-stu-id="e7f37-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="e7f37-108">Pour plus d’informations, consultez [les Modes de sélection dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e7f37-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="e7f37-109">Pour obtenir la cellule active par programme</span><span class="sxs-lookup"><span data-stu-id="e7f37-109">To get the current cell programmatically</span></span>  
  
-   <span data-ttu-id="e7f37-110">Utilisez le <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="e7f37-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="e7f37-111">Pour définir la cellule active par programmation</span><span class="sxs-lookup"><span data-stu-id="e7f37-111">To set the current cell programmatically</span></span>  
  
-   <span data-ttu-id="e7f37-112">Définir le <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété de la <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e7f37-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e7f37-113">Dans l’exemple de code suivant, la cellule active est définie à la ligne 0, colonne 1.</span><span class="sxs-lookup"><span data-stu-id="e7f37-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7f37-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e7f37-114">Compiling the Code</span></span>  
 <span data-ttu-id="e7f37-115">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="e7f37-115">This example requires:</span></span>  
  
-   <span data-ttu-id="e7f37-116"><xref:System.Windows.Forms.Button>contrôles nommés `getCurrentCellButton` et `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="e7f37-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="e7f37-117">Dans [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], vous devez joindre le <xref:System.Windows.Forms.Control.Click> événements pour chaque bouton au gestionnaire d’événements associé dans l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="e7f37-117">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
-   <span data-ttu-id="e7f37-118">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="e7f37-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="e7f37-119">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e7f37-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f37-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7f37-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e7f37-121">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7f37-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="e7f37-122">Modes de sélection dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7f37-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
