---
title: "Comment : héberger des contrôles dans des cellules DataGridView Windows Forms"
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
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7fd74b54a4e8c91762a3f32c6c89877470c10960
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="bbbb7-102">Comment : héberger des contrôles dans des cellules DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbbb7-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="bbbb7-103">Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plusieurs types de colonnes, ce qui permet à vos utilisateurs d'entrer et de modifier des valeurs de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="bbbb7-104">Toutefois, si ces types de colonnes ne répondent pas à vos besoins de saisie de données, vous pouvez créer vos propres types de colonnes avec des cellules qui hébergent les contrôles de votre choix.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="bbbb7-105">Pour cela, vous devez définir des classes qui dérivent de <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="bbbb7-106">Vous devez aussi définir une classe qui dérive de <xref:System.Windows.Forms.Control> et implémente l'interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="bbbb7-107">L'exemple de code suivant montre comment créer une colonne de calendrier.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="bbbb7-108">Les cellules de cette colonne affichent des dates dans des cellules de zone de texte ordinaires, mais quand l'utilisateur modifie une cellule, un contrôle <xref:System.Windows.Forms.DateTimePicker> apparaît.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="bbbb7-109">Pour éviter de devoir réimplémenter une fonctionnalité d'affichage de zone de texte, la classe `CalendarCell` dérive de la classe <xref:System.Windows.Forms.DataGridViewTextBoxCell> au lieu d'hériter directement de la classe <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbbb7-110">Quand vous dérivez de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> et que vous ajoutez de nouvelles propriétés à la classe dérivée, veillez à substituer la méthode `Clone` pour copier les nouvelles propriétés lors des opérations de clonage.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="bbbb7-111">Vous devez aussi appeler la méthode `Clone` de la classe de base pour que les propriétés de la classe de base soient copiées dans la nouvelle cellule ou colonne.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbbb7-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="bbbb7-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbbb7-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="bbbb7-113">Compiling the Code</span></span>  
 <span data-ttu-id="bbbb7-114">L'exemple suivant nécessite :</span><span class="sxs-lookup"><span data-stu-id="bbbb7-114">The following example requires:</span></span>  
  
-   <span data-ttu-id="bbbb7-115">des références aux assemblys System et System.Windows.Forms ;</span><span class="sxs-lookup"><span data-stu-id="bbbb7-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bbbb7-116">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bbbb7-116">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bbbb7-117">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="bbbb7-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="bbbb7-118">Consultez également [Guide pratique pour compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="bbbb7-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbb7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbbb7-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.DateTimePicker>  
 [<span data-ttu-id="bbbb7-120">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbbb7-120">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="bbbb7-121">Architecture du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="bbbb7-121">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [<span data-ttu-id="bbbb7-122">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbbb7-122">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
