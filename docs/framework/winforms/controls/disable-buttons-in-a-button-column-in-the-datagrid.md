---
title: "Comment : désactiver des boutons d'une colonne de boutons dans le contrôle DataGridView Windows Forms"
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
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c6f28ac69e2799a25f75c3093d9c8f1ef01bc48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1179e-102">Comment : désactiver des boutons d'une colonne de boutons dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1179e-102">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1179e-103">Le contrôle <xref:System.Windows.Forms.DataGridView> inclut la classe <xref:System.Windows.Forms.DataGridViewButtonCell> pour l'affichage des cellules avec une interface utilisateur telle qu'un bouton.</span><span class="sxs-lookup"><span data-stu-id="1179e-103">The <xref:System.Windows.Forms.DataGridView> control includes the <xref:System.Windows.Forms.DataGridViewButtonCell> class for displaying cells with a user interface (UI) like a button.</span></span> <span data-ttu-id="1179e-104">Toutefois, <xref:System.Windows.Forms.DataGridViewButtonCell> ne permet pas de désactiver l'apparence du bouton affiché par la cellule.</span><span class="sxs-lookup"><span data-stu-id="1179e-104">However, <xref:System.Windows.Forms.DataGridViewButtonCell> does not provide a way to disable the appearance of the button displayed by the cell.</span></span>  
  
 <span data-ttu-id="1179e-105">L'exemple de code suivant montre comment personnaliser la classe <xref:System.Windows.Forms.DataGridViewButtonCell> pour afficher des boutons qui peuvent apparaître désactivés.</span><span class="sxs-lookup"><span data-stu-id="1179e-105">The following code example demonstrates how to customize the <xref:System.Windows.Forms.DataGridViewButtonCell> class to display buttons that can appear disabled.</span></span> <span data-ttu-id="1179e-106">L'exemple définit un nouveau type de cellule, `DataGridViewDisableButtonCell`, qui dérive de <xref:System.Windows.Forms.DataGridViewButtonCell>.</span><span class="sxs-lookup"><span data-stu-id="1179e-106">The example defines a new cell type, `DataGridViewDisableButtonCell`, that derives from <xref:System.Windows.Forms.DataGridViewButtonCell>.</span></span> <span data-ttu-id="1179e-107">Ce type de cellule fournit une nouvelle propriété `Enabled` qui peut prendre la valeur `false` pour dessiner un bouton désactivé dans la cellule.</span><span class="sxs-lookup"><span data-stu-id="1179e-107">This cell type provides a new `Enabled` property that can be set to `false` to draw a disabled button in the cell.</span></span> <span data-ttu-id="1179e-108">L'exemple définit également un nouveau type de colonne, `DataGridViewDisableButtonColumn`, qui affiche des objets `DataGridViewDisableButtonCell`.</span><span class="sxs-lookup"><span data-stu-id="1179e-108">The example also defines a new column type, `DataGridViewDisableButtonColumn`, that displays `DataGridViewDisableButtonCell` objects.</span></span> <span data-ttu-id="1179e-109">Pour illustrer ce nouveau type de cellule et de colonne, la valeur actuelle de chaque <xref:System.Windows.Forms.DataGridViewCheckBoxCell> dans le <xref:System.Windows.Forms.DataGridView> parent détermine si la propriété  `Enabled` du `DataGridViewDisableButtonCell` sur la même ligne est `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="1179e-109">To demonstrate this new cell and column type, the current value of each <xref:System.Windows.Forms.DataGridViewCheckBoxCell> in the parent <xref:System.Windows.Forms.DataGridView> determines whether the `Enabled` property of the `DataGridViewDisableButtonCell` in the same row is `true` or `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1179e-110">Quand vous dérivez de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> et que vous ajoutez de nouvelles propriétés à la classe dérivée, veillez à substituer la méthode `Clone` pour copier les nouvelles propriétés lors des opérations de clonage.</span><span class="sxs-lookup"><span data-stu-id="1179e-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="1179e-111">Vous devez aussi appeler la méthode `Clone` de la classe de base pour que les propriétés de la classe de base soient copiées dans la nouvelle cellule ou colonne.</span><span class="sxs-lookup"><span data-stu-id="1179e-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1179e-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="1179e-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1179e-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="1179e-113">Compiling the Code</span></span>  
 <span data-ttu-id="1179e-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="1179e-114">This example requires:</span></span>  
  
-   <span data-ttu-id="1179e-115">Références aux assemblys System, System.Drawing, System.Windows.Forms et System.Windows.Forms.VisualStyles.</span><span class="sxs-lookup"><span data-stu-id="1179e-115">References to the System, System.Drawing, System.Windows.Forms and System.Windows.Forms.VisualStyles assemblies.</span></span>  
  
 <span data-ttu-id="1179e-116">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1179e-116">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1179e-117">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="1179e-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="1179e-118">Consultez également [Guide pratique pour compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1179e-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1179e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1179e-119">See Also</span></span>  
 [<span data-ttu-id="1179e-120">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1179e-120">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1179e-121">Architecture du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="1179e-121">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [<span data-ttu-id="1179e-122">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1179e-122">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
