---
title: "Comment : masquer des ToolStripMenuItems à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06a95581e156a7027c8fa0bda6e5fbc4babdb85b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="fbbfe-102">Comment : masquer des ToolStripMenuItems à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="fbbfe-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="fbbfe-103">Le masquage des éléments de menu est un moyen de contrôler l’interface utilisateur (IU) de votre application et de limiter les commandes de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="fbbfe-104">Souvent, vous devez masquer un menu quand tous les éléments de menu ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="fbbfe-105">Cela pose moins distractions pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="fbbfe-106">En outre, vous souhaiterez peut-être cacher et désactiver le menu ou un élément de menu, comme simple masquage n’empêche pas l’utilisateur d’accéder à une commande de menu à l’aide d’une touche de raccourci.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="fbbfe-107">Pour plus d’informations sur la désactivation des éléments de menu, consultez [Comment : désactiver des ToolStripMenuItems à l’aide du concepteur](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="fbbfe-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbbfe-108">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fbbfe-109">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="fbbfe-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fbbfe-110">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="fbbfe-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="fbbfe-111">Pour masquer un menu de niveau supérieur et ses éléments de sous-menu</span><span class="sxs-lookup"><span data-stu-id="fbbfe-111">To hide a top-level menu and its submenu items</span></span>  
  
1.  <span data-ttu-id="fbbfe-112">Sélectionnez l’élément de menu de niveau supérieur et définissez son <xref:System.Windows.Forms.ToolStripItem.Visible%2A> ou <xref:System.Windows.Forms.ToolStripItem.Available%2A> propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="fbbfe-113">Lorsque vous masquez l’élément de menu de niveau supérieur, tous les éléments de menu dans ce menu sont également masqués.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="fbbfe-114">Si vous cliquez quelque part autre que sur le <xref:System.Windows.Forms.MenuStrip> après avoir défini <xref:System.Windows.Forms.ToolStripItem.Visible%2A> à `false`, l’élément de menu de niveau supérieur entier et ses éléments de sous-menu disparaissent de votre formulaire, vous montrant ainsi l’effet de l’exécution de votre action.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="fbbfe-115">Pour afficher l’élément de menu de niveau supérieur masqué au moment du design, cliquez sur le <xref:System.Windows.Forms.MenuStrip> dans les **barre d’état du composant**, dans **structure du Document**, ou en haut de la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbbfe-116">Vous allez masquer rarement d’un menu à l’exception de plusieurs menus enfants MDI (interface) de document dans un scénario de fusion.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="fbbfe-117">Pour masquer un élément de sous-menu</span><span class="sxs-lookup"><span data-stu-id="fbbfe-117">To hide a submenu item</span></span>  
  
1.  <span data-ttu-id="fbbfe-118">Sélectionnez l’élément de sous-menu et définissez son <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="fbbfe-119">Lorsque vous masquez un élément de sous-menu, il reste visible sur votre formulaire au moment du design afin que vous pouvez facilement le sélectionner pour le travail supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="fbbfe-120">Il est en fait masqué au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fbbfe-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbfe-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbbfe-121">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [<span data-ttu-id="fbbfe-122">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="fbbfe-122">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="fbbfe-123">Guide pratique pour désactiver des ToolStripMenuItems à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="fbbfe-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
