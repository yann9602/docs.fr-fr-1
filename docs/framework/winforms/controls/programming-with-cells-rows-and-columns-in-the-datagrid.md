---
title: "Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], elements
- columns [Windows Forms], data grids
- cells [Windows Forms], data grids
- DataGridView control [Windows Forms], programming with grid elements
- rows [Windows Forms], data grids
ms.assetid: 0d76f7e4-4149-42c6-9118-bb37d6669dc5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 313867b76d569fb98b1bd5d46c658763d0020726
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="programming-with-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2d9f8-102">Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d9f8-102">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2d9f8-103">Cette section fournit des rubriques qui montrent comment effectuer des tâches de programmation différents impliquant des cellules, lignes et les objets de colonne.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-103">This section provides topics that demonstrate various programming tasks involving cell, row, and column objects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d9f8-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2d9f8-104">In This Section</span></span>  
 [<span data-ttu-id="2d9f8-105">Guide pratique pour ajouter des info-bulles à des cellules dans un contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d9f8-105">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/add-tooltips-to-individual-cells-in-a-wf-datagridview-control.md)  
 <span data-ttu-id="2d9f8-106">Décrit comment gérer les <xref:System.Windows.Forms.DataGridView.CellFormatting> événements pour fournir différentes info-bulles pour les cellules individuelles.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-106">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting> event to provide different ToolTips for individual cells.</span></span>  
  
 [<span data-ttu-id="2d9f8-107">Guide pratique pour exécuter une action personnalisée basée sur les modifications apportées dans une cellule d'un contrôle DataGridView Windows Form</span><span class="sxs-lookup"><span data-stu-id="2d9f8-107">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/perform-a-custom-action-based-on-changes-in-a-cell-of-a-datagrid.md)  
 <span data-ttu-id="2d9f8-108">Décrit comment gérer les <xref:System.Windows.Forms.DataGridView.CellValueChanged> et <xref:System.Windows.Forms.DataGridView.CellStateChanged> les événements.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-108">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
 [<span data-ttu-id="2d9f8-109">Guide pratique pour manipuler des bandes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d9f8-109">How to: Manipulate Bands in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-bands-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="2d9f8-110">Explique comment programmer avec les objets de type <xref:System.Windows.Forms.DataGridViewBand>, qui est le type de base pour les lignes et colonnes.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-110">Describes how to program with objects of type <xref:System.Windows.Forms.DataGridViewBand>, which is the base type for rows and columns.</span></span>  
  
 [<span data-ttu-id="2d9f8-111">Guide pratique pour manipuler les lignes du contrôle DataGridView Windows Formsligne</span><span class="sxs-lookup"><span data-stu-id="2d9f8-111">How to: Manipulate Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="2d9f8-112">Explique comment programmer avec les objets de type `DataGridViewRow`.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-112">Describes how to program with objects of type `DataGridViewRow`.</span></span>  
  
 [<span data-ttu-id="2d9f8-113">Guide pratique pour manipuler les colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d9f8-113">How to: Manipulate Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="2d9f8-114">Explique comment programmer avec les objets de type `DataGridViewColumn`.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-114">Describes how to program with objects of type `DataGridViewColumn`.</span></span>  
  
 [<span data-ttu-id="2d9f8-115">Guide pratique pour utiliser des colonnes de type image dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d9f8-115">How to: Work with Image Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="2d9f8-116">Explique comment programmer avec la `DataGridViewImageColumn` classe.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-116">Describes how to program with the `DataGridViewImageColumn` class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2d9f8-117">Référence</span><span class="sxs-lookup"><span data-stu-id="2d9f8-117">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="2d9f8-118">Fournit la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="2d9f8-119">Fournit la documentation de référence pour la <xref:System.Windows.Forms.DataGridViewCell> classe.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="2d9f8-120">Fournit la documentation de référence pour la <xref:System.Windows.Forms.DataGridViewRow> classe.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="2d9f8-121">Fournit la documentation de référence pour la <xref:System.Windows.Forms.DataGridViewColumn> classe.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2d9f8-122">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="2d9f8-122">Related Sections</span></span>  
 [<span data-ttu-id="2d9f8-123">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d9f8-123">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="2d9f8-124">Fournit des rubriques qui décrivent couramment utilisé des propriétés de cellule, ligne et colonne.</span><span class="sxs-lookup"><span data-stu-id="2d9f8-124">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9f8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d9f8-125">See Also</span></span>  
 [<span data-ttu-id="2d9f8-126">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="2d9f8-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="2d9f8-127">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d9f8-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
