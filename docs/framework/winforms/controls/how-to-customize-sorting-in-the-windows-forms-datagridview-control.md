---
title: "Comment : personnaliser le tri dans le contrôle DataGridView Windows Forms"
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
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3ea4c7ccd215bed9bd31e0cd5155209fddcc7b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6b7ef-102">Comment : personnaliser le tri dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b7ef-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6b7ef-103">Le contrôle <xref:System.Windows.Forms.DataGridView> assure le tri automatique mais, selon vos besoins, vous devrez peut-être personnaliser les opérations de tri.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="6b7ef-104">Par exemple, vous pouvez utiliser le tri par programmation pour créer une autre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="6b7ef-105">Vous pouvez également gérer l'événement <xref:System.Windows.Forms.DataGridView.SortCompare> ou appeler la surcharge `Sort(IComparer)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A> pour bénéficier d'une plus grande flexibilité de tri, par exemple pour trier plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="6b7ef-106">Les exemples de code suivants illustrent ces trois approches de tri personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="6b7ef-107">Pour plus d’informations, consultez [Modes de tri des colonnes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6b7ef-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="6b7ef-108">Tri par programmation</span><span class="sxs-lookup"><span data-stu-id="6b7ef-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="6b7ef-109">L'exemple de code suivant illustre un tri par programmation qui fait appel aux propriétés <xref:System.Windows.Forms.DataGridView.SortOrder%2A> et <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> pour déterminer le sens du tri et à la propriété <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> pour définir manuellement le glyphe de tri.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="6b7ef-110">La surcharge `Sort(DataGridViewColumn,ListSortDirection)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A> sert à trier les données dans une seule colonne.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="6b7ef-111">Tri personnalisé à l'aide de l'événement SortCompare</span><span class="sxs-lookup"><span data-stu-id="6b7ef-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="6b7ef-112">L'exemple de code suivant illustre un tri personnalisé qui fait appel à un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.SortCompare>.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="6b7ef-113">Le <xref:System.Windows.Forms.DataGridViewColumn> sélectionné est trié et, si la colonne contient des valeurs en double, l'ID de colonne est utilisé pour déterminer l'ordre final.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="6b7ef-114">Tri personnalisé à l'aide de l'interface IComparer</span><span class="sxs-lookup"><span data-stu-id="6b7ef-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="6b7ef-115">L'exemple de code suivant illustre un tri personnalisé qui fait appel à la surcharge `Sort(IComparer)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>, qui prend une implémentation de l'interface <xref:System.Collections.IComparer> pour effectuer un tri sur plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b7ef-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6b7ef-116">Compiling the Code</span></span>  
 <span data-ttu-id="6b7ef-117">Ces exemples nécessitent :</span><span class="sxs-lookup"><span data-stu-id="6b7ef-117">These examples require:</span></span>  
  
-   <span data-ttu-id="6b7ef-118">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6b7ef-119">Pour plus d’informations sur la création de ces exemples à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6b7ef-119">For information about building these examples from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6b7ef-120">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="6b7ef-120">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="6b7ef-121">Consultez également [Guide pratique pour compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6b7ef-121">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b7ef-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b7ef-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="6b7ef-123">Tri des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b7ef-123">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6b7ef-124">Modes de tri des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b7ef-124">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6b7ef-125">Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b7ef-125">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
