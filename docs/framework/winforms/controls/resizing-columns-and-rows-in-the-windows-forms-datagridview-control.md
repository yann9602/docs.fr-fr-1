---
title: "Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3621b05f1faae671d93106f50dfef1311959e48e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="14eba-102">Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14eba-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="14eba-103">Le `DataGridView` contrôle fournit de nombreuses options pour personnaliser le comportement de dimensionnement de ses colonnes et de lignes.</span><span class="sxs-lookup"><span data-stu-id="14eba-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="14eba-104">En règle générale, `DataGridView` cellules ne se redimensionnent pas en fonction de leur contenu.</span><span class="sxs-lookup"><span data-stu-id="14eba-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="14eba-105">Au lieu de cela, elles tronquent toute valeur d’affichage qui est supérieure à la cellule.</span><span class="sxs-lookup"><span data-stu-id="14eba-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="14eba-106">Si le contenu peut être affiché sous forme de chaîne, la cellule affiche dans une info-bulle.</span><span class="sxs-lookup"><span data-stu-id="14eba-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="14eba-107">Par défaut, les utilisateurs peuvent faire glisser les séparateurs d’en-tête avec la souris pour afficher plus d’informations, ligne et colonne.</span><span class="sxs-lookup"><span data-stu-id="14eba-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="14eba-108">Les utilisateurs peuvent double-cliquer également un séparateur pour redimensionner automatiquement la bande de ligne, de colonne ou en-tête associée en fonction de son contenu.</span><span class="sxs-lookup"><span data-stu-id="14eba-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="14eba-109">Le `DataGridView` contrôle fournit des propriétés, méthodes et événements qui vous permettent de personnaliser ou de désactiver tous ces comportements dirigés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="14eba-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="14eba-110">En outre, vous pouvez redimensionner par programme des lignes, colonnes et en-têtes pour s’adapter à leur contenu, ou vous pouvez les configurer pour être redimensionnées automatiquement chaque fois que leur contenu change.</span><span class="sxs-lookup"><span data-stu-id="14eba-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="14eba-111">Vous pouvez également configurer des colonnes pour diviser automatiquement la largeur disponible du contrôle dans les proportions que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="14eba-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14eba-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="14eba-112">In This Section</span></span>  
 [<span data-ttu-id="14eba-113">Options de dimensionnement dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14eba-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="14eba-114">Décrit les options de redimensionnement de lignes, colonnes et des en-têtes.</span><span class="sxs-lookup"><span data-stu-id="14eba-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="14eba-115">Également fournit des détails sur les méthodes et propriétés liées au dimensionnement et décrit les scénarios d’utilisation courants.</span><span class="sxs-lookup"><span data-stu-id="14eba-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="14eba-116">Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14eba-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="14eba-117">Décrit le mode de remplissage de colonne en détail et fournit du code de démonstration que vous pouvez utiliser pour faire des essais avec le mode de remplissage de colonne et les autres modes.</span><span class="sxs-lookup"><span data-stu-id="14eba-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="14eba-118">Guide pratique pour définir les modes de redimensionnement du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14eba-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="14eba-119">Décrit comment configurer les modes de dimensionnement pour des objectifs communs.</span><span class="sxs-lookup"><span data-stu-id="14eba-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="14eba-120">Guide pratique pour redimensionner des cellules par programme pour les adapter au contenu du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14eba-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="14eba-121">Fournit du code de démonstration que vous pouvez utiliser pour faire des essais avec le redimensionnement par programmation.</span><span class="sxs-lookup"><span data-stu-id="14eba-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="14eba-122">Guide pratique pour redimensionner automatiquement des cellules lorsque leur contenu change dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14eba-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="14eba-123">Fournit du code de démonstration que vous pouvez utiliser pour faire des essais avec les modes de dimensionnement automatique.</span><span class="sxs-lookup"><span data-stu-id="14eba-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="14eba-124">Référence</span><span class="sxs-lookup"><span data-stu-id="14eba-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="14eba-125">Fournit la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="14eba-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14eba-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14eba-126">See Also</span></span>  
 [<span data-ttu-id="14eba-127">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="14eba-127">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
