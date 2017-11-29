---
title: "Comment : spécifier le mode édition pour le contrôle DataGridView Windows Forms"
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
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70bf241865eef3366444e1b4dc20c19adaff983e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="9ceb9-102">Comment : spécifier le mode édition pour le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ceb9-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9ceb9-103">Par défaut, les utilisateurs peuvent modifier le contenu d’actuel <xref:System.Windows.Forms.DataGridView> cellule de zone de texte en tapant qu’il contient ou en appuyant sur F2.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="9ceb9-104">Cela met la cellule en mode édition si toutes les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="9ceb9-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="9ceb9-105">La source de données sous-jacente prend en charge la modification.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-105">The underlying data source supports editing.</span></span>  
  
-   <span data-ttu-id="9ceb9-106">Le <xref:System.Windows.Forms.DataGridView> le contrôle est activé.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
-   <span data-ttu-id="9ceb9-107">Le <xref:System.Windows.Forms.DataGridView.EditMode%2A> valeur de propriété n’est pas <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
-   <span data-ttu-id="9ceb9-108">Le `ReadOnly` propriétés de cellule, de ligne, de colonne et de contrôle sont tous définis sur `false`.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="9ceb9-109">En mode édition, l’utilisateur peut modifier la valeur de cellule et appuyez sur ENTRÉE pour valider la modification ou la touche ÉCHAP pour rétablir sa valeur d’origine de la cellule.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="9ceb9-110">Vous pouvez configurer un <xref:System.Windows.Forms.DataGridView> permettant à une cellule passe en mode édition dès qu’elle devient la cellule active.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="9ceb9-111">Le comportement des touches entrée et ÉCHAP est inchangé dans ce cas, mais la cellule reste en mode édition après que la valeur est validée ou annulée.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="9ceb9-112">Vous pouvez également configurer le contrôle afin que les cellules entrer en mode Édition uniquement lorsque les utilisateurs entrent dans la cellule ou uniquement lorsque les utilisateurs appuient sur F2.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="9ceb9-113">Enfin, vous pouvez empêcher des cellules à partir de l’entrée en mode d’édition, sauf lorsque vous appelez le <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="9ceb9-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="9ceb9-114">Pour modifier le mode d’édition d’un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="9ceb9-114">To change the edit mode of a DataGridView control</span></span>  
  
-   <span data-ttu-id="9ceb9-115">Définir le <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> propriété approprié <xref:System.Windows.Forms.DataGridViewEditMode> énumération.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ceb9-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9ceb9-116">Compiling the Code</span></span>  
 <span data-ttu-id="9ceb9-117">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="9ceb9-117">This example requires:</span></span>  
  
-   <span data-ttu-id="9ceb9-118">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="9ceb9-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="9ceb9-119">des références aux assemblys <xref:System> et <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="9ceb9-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ceb9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ceb9-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="9ceb9-121">Saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ceb9-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
