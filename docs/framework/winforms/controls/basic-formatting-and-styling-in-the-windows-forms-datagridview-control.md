---
title: "Mises en forme et styles de base dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fa5c240adaaf6512cfbd6b7bd0796bd0983a530
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="95f9b-102">Mises en forme et styles de base dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="95f9b-103">Le `DataGridView` contrôle vous permet de définir l’apparence de base des cellules et le format d’affichage des valeurs de cellule.</span><span class="sxs-lookup"><span data-stu-id="95f9b-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="95f9b-104">Vous pouvez définir d’apparence et la mise en forme de styles pour les cellules individuelles, pour les cellules dans des colonnes spécifiques et des lignes ou pour toutes les cellules dans le contrôle en définissant les propriétés de la `DataGridViewCellStyle` objets accédés par divers `DataGridView` propriétés du contrôle.</span><span class="sxs-lookup"><span data-stu-id="95f9b-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="95f9b-105">En outre, vous pouvez modifier ces styles de façon dynamique en fonction de facteurs tels que la valeur de cellule en gérant le `CellFormatting` événement.</span><span class="sxs-lookup"><span data-stu-id="95f9b-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95f9b-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="95f9b-106">In This Section</span></span>  
 [<span data-ttu-id="95f9b-107">Guide pratique pour modifier les styles de bordures et de quadrillage dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="95f9b-108">Explique comment définir `DataGridView` propriétés qui définissent l’apparence de la bordure du contrôle et les lignes de la limite entre les cellules.</span><span class="sxs-lookup"><span data-stu-id="95f9b-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="95f9b-109">Styles de cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="95f9b-110">Décrit la `DataGridViewCellStyle` classe et comment les propriétés de ce type interagissent pour définir comment les cellules sont affichées dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="95f9b-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="95f9b-111">Guide pratique pour définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="95f9b-112">Décrit comment utiliser `DataGridViewCellStyle` propriétés pour définir l’apparence par défaut des cellules dans les lignes et colonnes spécifiques et dans l’ensemble du contrôle.</span><span class="sxs-lookup"><span data-stu-id="95f9b-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="95f9b-113">Guide pratique pour mettre en forme des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="95f9b-114">Décrit comment mettre en forme les valeurs d’affichage de cellule à l’aide de `DataGridViewCellStyle` propriétés.</span><span class="sxs-lookup"><span data-stu-id="95f9b-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="95f9b-115">Guide pratique pour définir des styles de police et de couleur dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="95f9b-116">Décrit comment utiliser le `DefaultCellStyle` propriété à définir base afficher les caractéristiques pour toutes les cellules dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="95f9b-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="95f9b-117">Guide pratique pour définir des styles de lignes en alternance pour le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="95f9b-118">Décrit comment créer un effet de type livre comptable dans le contrôle à l’aide de lignes en alternance qui sont affichent différemment.</span><span class="sxs-lookup"><span data-stu-id="95f9b-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="95f9b-119">Guide pratique pour utiliser le modèle de ligne pour personnaliser les lignes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="95f9b-120">Décrit comment utiliser le `RowTemplate` propriété à définir les propriétés de ligne qui seront utilisées pour toutes les lignes dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="95f9b-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="95f9b-121">Référence</span><span class="sxs-lookup"><span data-stu-id="95f9b-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="95f9b-122">Fournit la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="95f9b-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="95f9b-123">Fournit la documentation de référence pour la <xref:System.Windows.Forms.DataGridViewCellStyle> classe.</span><span class="sxs-lookup"><span data-stu-id="95f9b-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="95f9b-124">Fournit la documentation de référence pour le <xref:System.Windows.Forms.DataGridView.CellFormatting> événement.</span><span class="sxs-lookup"><span data-stu-id="95f9b-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="95f9b-125">Fournit la documentation de référence pour le <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="95f9b-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="95f9b-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="95f9b-126">Related Sections</span></span>  
 [<span data-ttu-id="95f9b-127">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-127">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="95f9b-128">Fournit des rubriques qui décrivent la peinture personnalisée des cellules et des lignes <xref:System.Windows.Forms.DataGridView> et la création de types de lignes, de colonnes et de cellules dérivés.</span><span class="sxs-lookup"><span data-stu-id="95f9b-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="95f9b-129">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95f9b-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="95f9b-130">Fournit des rubriques qui décrivent couramment utilisé des propriétés de cellule, ligne et colonne.</span><span class="sxs-lookup"><span data-stu-id="95f9b-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f9b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95f9b-131">See Also</span></span>  
 [<span data-ttu-id="95f9b-132">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="95f9b-132">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
