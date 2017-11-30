---
title: "Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eebd0f36fbf1bf3bfc37b8fa836d318a9b8ac007
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4e058-102">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4e058-103">Nombreux comportements de base de `DataGridView` cellules, lignes et colonnes peuvent être modifiés en définissant les propriétés uniques.</span><span class="sxs-lookup"><span data-stu-id="4e058-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="4e058-104">Les rubriques de cette section décrivent plusieurs de ces fonctionnalités les plus couramment utilisés.</span><span class="sxs-lookup"><span data-stu-id="4e058-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e058-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4e058-105">In This Section</span></span>  
 [<span data-ttu-id="4e058-106">Guide pratique pour masquer des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4e058-107">Décrit comment empêcher des colonnes spécifiques dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4e058-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="4e058-108">Guide pratique pour masquer les en-têtes de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4e058-109">Décrit comment empêcher les en-têtes de colonnes dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4e058-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="4e058-110">Guide pratique pour activer la réorganisation des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4e058-111">Décrit comment permettre aux utilisateurs de réorganiser les colonnes dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4e058-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="4e058-112">Guide pratique pour figer les colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4e058-113">Décrit comment empêcher une ou plusieurs colonnes adjacentes de défilement.</span><span class="sxs-lookup"><span data-stu-id="4e058-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="4e058-114">Guide pratique pour définir une colonne en lecture seule dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4e058-115">Décrit comment empêcher les utilisateurs de modifier des colonnes spécifiques dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4e058-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="4e058-116">Guide pratique pour empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="4e058-117">Décrit comment supprimer la ligne pour les nouveaux enregistrements en bas du contrôle pour empêcher les utilisateurs d’ajouter des lignes.</span><span class="sxs-lookup"><span data-stu-id="4e058-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="4e058-118">Décrit également comment empêcher les utilisateurs de supprimer des lignes.</span><span class="sxs-lookup"><span data-stu-id="4e058-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="4e058-119">Guide pratique pour obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="4e058-120">Décrit comment accéder à la cellule qui a actuellement le focus dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4e058-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="4e058-121">Comment : afficher des images dans les cellules du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4e058-122">Décrit comment créer une colonne d’image qui affiche une icône dans chaque cellule.</span><span class="sxs-lookup"><span data-stu-id="4e058-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4e058-123">Référence</span><span class="sxs-lookup"><span data-stu-id="4e058-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="4e058-124">Fournit la documentation de référence pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4e058-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4e058-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="4e058-125">Related Sections</span></span>  
 [<span data-ttu-id="4e058-126">Mises en forme et styles de base dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4e058-127">Fournit des rubriques qui décrivent comment modifier l'apparence de base du contrôle et le format d'affichage des données de cellules.</span><span class="sxs-lookup"><span data-stu-id="4e058-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="4e058-128">Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="4e058-129">Fournit des rubriques qui expliquent comment programmer avec des objets de colonnes, de lignes et de cellules.</span><span class="sxs-lookup"><span data-stu-id="4e058-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e058-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e058-130">See Also</span></span>  
 [<span data-ttu-id="4e058-131">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="4e058-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="4e058-132">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e058-132">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
