---
title: "Comment : afficher des cases d'option dans un MenuStrip (Windows Forms)"
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
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0de3b8596bc06c79f391141ef85fec65ac343d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="c7cbd-102">Comment : afficher des cases d'option dans un MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c7cbd-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="c7cbd-103">Cases d’option, également appelé cases sont similaires aux cases à cocher, sauf que les utilisateurs peuvent sélectionner qu’un seul à la fois.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="c7cbd-104">Bien que, par défaut le <xref:System.Windows.Forms.ToolStripMenuItem> classe ne fournit pas de comportement de case d’option, la classe fournit un comportement de case à cocher que vous pouvez personnaliser pour implémenter un comportement de case d’option pour les éléments de menu dans un <xref:System.Windows.Forms.MenuStrip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="c7cbd-105">Lorsque le <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriété d’un élément de menu est `true`, les utilisateurs peuvent cliquer sur l’élément pour basculer l’affichage de la case à cocher correspondante.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="c7cbd-106">Le <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriété indique l’état actuel de l’élément.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="c7cbd-107">Pour implémenter le comportement de case d’option de base, vous devez vous assurer que lorsqu’un élément est sélectionné, le <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriété pour l’élément sélectionné précédemment à `false`.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="c7cbd-108">Les procédures suivantes décrivent comment implémenter cette et des fonctionnalités supplémentaires dans une classe qui hérite de la <xref:System.Windows.Forms.ToolStripMenuItem> classe.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="c7cbd-109">Le `ToolStripRadioButtonMenuItem` classe remplace les membres comme <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> et <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pour fournir le comportement de la sélection et l’apparence des cases d’option.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="c7cbd-110">En outre, cette classe substitue le <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriété afin que les options d’un sous-menu sont désactivées, sauf si l’élément parent est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="c7cbd-111">Pour implémenter le comportement de sélection de case d’option</span><span class="sxs-lookup"><span data-stu-id="c7cbd-111">To implement option-button selection behavior</span></span>  
  
1.  <span data-ttu-id="c7cbd-112">Initialiser le <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriété `true` pour activer la sélection de l’élément.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  <span data-ttu-id="c7cbd-113">Remplacer la <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> méthode pour effacer la sélection de l’élément sélectionné précédemment lorsqu’un nouvel élément est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  <span data-ttu-id="c7cbd-114">Remplacer le <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> pour s’assurer qu’un élément qui a déjà été sélectionné un clic sur n’effacera pas la sélection.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="c7cbd-115">Pour modifier l’apparence des éléments de case d’option</span><span class="sxs-lookup"><span data-stu-id="c7cbd-115">To modify the appearance of the option-button items</span></span>  
  
1.  <span data-ttu-id="c7cbd-116">Remplacer la <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> méthode pour remplacer la coche par défaut avec une case d’option à l’aide de la <xref:System.Windows.Forms.RadioButtonRenderer> classe.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  <span data-ttu-id="c7cbd-117">Remplacer la <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, et <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> méthodes pour effectuer le suivi de l’état de la souris et vérifiez que le <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> méthode peint l’état de la case d’option correct.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="c7cbd-118">Pour désactiver les options d’un sous-menu lorsque l’élément parent n’est pas sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1.  <span data-ttu-id="c7cbd-119">Remplacer la <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriété afin que l’élément est désactivé lorsqu’il a un élément parent avec à la fois un <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> valeur `true` et un <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> valeur de `false`.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  <span data-ttu-id="c7cbd-120">Remplacer la <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> méthode pour vous abonner à la <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> les événements de l’élément parent.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  <span data-ttu-id="c7cbd-121">Dans le Gestionnaire de l’élément parent <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> événement, l’élément pour mettre à jour l’affichage avec le nouvel état activé.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="c7cbd-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7cbd-122">Example</span></span>  
 <span data-ttu-id="c7cbd-123">L’exemple de code suivant fournit le texte complet `ToolStripRadioButtonMenuItem` (classe) et un <xref:System.Windows.Forms.Form> classe et `Program` classe pour illustrer le comportement de case d’option.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7cbd-124">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c7cbd-124">Compiling the Code</span></span>  
 <span data-ttu-id="c7cbd-125">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="c7cbd-125">This example requires:</span></span>  
  
-   <span data-ttu-id="c7cbd-126">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="c7cbd-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7cbd-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7cbd-127">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [<span data-ttu-id="c7cbd-128">MenuStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="c7cbd-128">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [<span data-ttu-id="c7cbd-129">Guide pratique pour implémenter un ToolStripRenderer personnalisé</span><span class="sxs-lookup"><span data-stu-id="c7cbd-129">How to: Implement a Custom ToolStripRenderer</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
