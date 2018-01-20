---
title: "Comment : figer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33606cc30ccc1d63e780d07bcb1757d62b7ebea2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="229a2-102">Comment : figer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="229a2-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="229a2-103">Quand des utilisateurs consultent des données affichées dans un contrôle Windows Forms <xref:System.Windows.Forms.DataGridView>, ils doivent parfois faire fréquemment référence à une même colonne ou un même ensemble de colonnes.</span><span class="sxs-lookup"><span data-stu-id="229a2-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="229a2-104">Par exemple, lorsque vous affichez une table des informations client qui contient de nombreuses colonnes, il est utile pour afficher le nom du client en permanence tout en laissant d’autres colonnes défiler à l’extérieur de la zone visible.</span><span class="sxs-lookup"><span data-stu-id="229a2-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="229a2-105">Pour obtenir ce comportement, vous pouvez figer des colonnes dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="229a2-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="229a2-106">Quand vous figez une colonne, toutes les colonnes à sa gauche (ou à sa droite dans les scripts de droite à gauche) sont aussi figées.</span><span class="sxs-lookup"><span data-stu-id="229a2-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="229a2-107">Les colonnes figées restent en place, tandis que toutes les autres colonnes peuvent défiler.</span><span class="sxs-lookup"><span data-stu-id="229a2-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="229a2-108">Si la réorganisation des colonnes est activée, les colonnes figées sont traitées comme un groupe distinct des colonnes non figées.</span><span class="sxs-lookup"><span data-stu-id="229a2-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="229a2-109">Les utilisateurs peuvent repositionner des colonnes dans l'un ou l'autre groupe, mais ils ne peuvent pas déplacer une colonne d'un groupe à l'autre.</span><span class="sxs-lookup"><span data-stu-id="229a2-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="229a2-110">La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="229a2-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="229a2-111">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="229a2-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="229a2-112">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="229a2-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="229a2-113">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="229a2-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="229a2-114">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="229a2-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="229a2-115">Pour figer une colonne à l’aide du Concepteur</span><span class="sxs-lookup"><span data-stu-id="229a2-115">To freeze a column using the designer</span></span>  
  
1.  <span data-ttu-id="229a2-116">Cliquez sur le glyphe de balise active (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit de la <xref:System.Windows.Forms.DataGridView> contrôler, puis sélectionnez **modifier les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="229a2-116">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="229a2-117">Sélectionnez une colonne dans la **colonnes sélectionnées** liste.</span><span class="sxs-lookup"><span data-stu-id="229a2-117">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="229a2-118">Dans le **propriétés de la colonne** grille, définissez la <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="229a2-118">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="229a2-119">Vous pouvez également figer une colonne lors de son ajout en sélectionnant la **figés** zone le **ajouter une colonne** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="229a2-119">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="229a2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="229a2-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="229a2-121">Guide pratique pour ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="229a2-121">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="229a2-122">Guide pratique pour activer la réorganisation des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="229a2-122">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="229a2-123">Comment : afficher du texte de droite à gauche dans les Windows Forms pour la globalisation</span><span class="sxs-lookup"><span data-stu-id="229a2-123">How to: Display Right-to-Left Text in Windows Forms for Globalization</span></span>](http://msdn.microsoft.com/library/f0663385-2354-4c65-8676-706422283b14)  
 [<span data-ttu-id="229a2-124">Comment : créer un projet d’Application Windows</span><span class="sxs-lookup"><span data-stu-id="229a2-124">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="229a2-125">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="229a2-125">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
