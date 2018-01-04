---
title: "Comment : Gérer le dépassement de capacité de contrôles ToolStrip dans les Windows Forms"
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
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 619c4832626693a56280c70af3ade5dbb9e9d4de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="1d523-102">Comment : Gérer le dépassement de capacité de contrôles ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d523-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>
<span data-ttu-id="1d523-103">Lorsque tous les éléments sur un <xref:System.Windows.Forms.ToolStrip> contrôle ne tiennent pas dans l’espace alloué, vous pouvez activer la fonctionnalité de dépassement sur les <xref:System.Windows.Forms.ToolStrip> et déterminent le comportement de dépassement de capacité de spécifiques <xref:System.Windows.Forms.ToolStripItem>s.</span><span class="sxs-lookup"><span data-stu-id="1d523-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>  
  
 <span data-ttu-id="1d523-104">Lorsque vous ajoutez <xref:System.Windows.Forms.ToolStripItem>qui requièrent davantage d’espace est alloué à la <xref:System.Windows.Forms.ToolStrip> étant donné la taille du formulaire en cours, une <xref:System.Windows.Forms.ToolStripOverflowButton> apparaît automatiquement dans le <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="1d523-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="1d523-105">Le <xref:System.Windows.Forms.ToolStripOverflowButton> s’affiche, et activé de dépassement de capacité des éléments sont déplacés dans le menu de dépassement de capacité de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="1d523-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="1d523-106">Cela vous permet de personnaliser et de hiérarchiser comment votre <xref:System.Windows.Forms.ToolStrip> éléments s’ajustent aux différentes tailles de formulaire.</span><span class="sxs-lookup"><span data-stu-id="1d523-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="1d523-107">Vous pouvez également modifier l’apparence de vos éléments lorsqu’elles se trouvent dans le dépassement de capacité à l’aide de la <xref:System.Windows.Forms.ToolStripItem.Placement%2A> et <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> propriétés et le <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement.</span><span class="sxs-lookup"><span data-stu-id="1d523-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="1d523-108">Si vous agrandissez le formulaire au moment du design ou au moment de l’exécution, plus <xref:System.Windows.Forms.ToolStripItem>peuvent être affichés sur le principal <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripOverflowButton> peut même disparaître jusqu'à ce que vous réduisez la taille du formulaire.</span><span class="sxs-lookup"><span data-stu-id="1d523-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="1d523-109">Pour activer le dépassement de capacité sur un contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1d523-109">To enable overflow on a ToolStrip control</span></span>  
  
-   <span data-ttu-id="1d523-110">Vérifiez que le <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> propriété n’est pas définie sur `false` pour le <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="1d523-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="1d523-111">La valeur par défaut est `True`.</span><span class="sxs-lookup"><span data-stu-id="1d523-111">The default is `True`.</span></span>  
  
     <span data-ttu-id="1d523-112">Lorsque <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> est `True` (la valeur par défaut), un <xref:System.Windows.Forms.ToolStripItem> est envoyé dans le menu de dépassement de capacité de liste déroulante lorsque le contenu de la <xref:System.Windows.Forms.ToolStripItem> dépasse la largeur d’un bouton horizontal <xref:System.Windows.Forms.ToolStrip> ou la hauteur d’un vertical <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="1d523-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="1d523-113">Pour spécifier le comportement de dépassement de capacité d’un ToolStripItem spécifique</span><span class="sxs-lookup"><span data-stu-id="1d523-113">To specify overflow behavior of a specific ToolStripItem</span></span>  
  
-   <span data-ttu-id="1d523-114">Définir le <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriété de la <xref:System.Windows.Forms.ToolStripItem> la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="1d523-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="1d523-115">Les possibilités sont `Always`, `Never`, et `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="1d523-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="1d523-116">Le defaultis `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="1d523-116">The defaultis `AsNeeded`.</span></span>  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1d523-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d523-117">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [<span data-ttu-id="1d523-118">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1d523-118">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="1d523-119">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1d523-119">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="1d523-120">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1d523-120">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
