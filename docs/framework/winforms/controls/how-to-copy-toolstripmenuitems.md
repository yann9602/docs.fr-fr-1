---
title: 'Comment : copier des ToolStripMenuItems'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77f48d7af76cc65092e9045ab76654c96a1a7c02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="7101e-102">Comment : copier des ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="7101e-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="7101e-103">Au moment du design, vous pouvez copier la totalité des menus du plus haut niveau et leurs éléments de sous-menu à un autre emplacement sur la <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="7101e-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="7101e-104">Vous pouvez également copier des éléments de menu individuels entre des menus du plus haut niveau ou changer la position des éléments de menu dans un menu.</span><span class="sxs-lookup"><span data-stu-id="7101e-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="7101e-105">Pour copier un menu du plus haut niveau et ses éléments de sous-menu vers un autre emplacement du plus haut niveau</span><span class="sxs-lookup"><span data-stu-id="7101e-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="7101e-106">Cliquez sur le menu que vous voulez copier et appuyez sur Ctrl+C, ou cliquez avec le bouton droit sur le menu et sélectionnez **Copier** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7101e-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="7101e-107">Cliquez sur le menu du plus haut niveau qui se trouve après le nouvel emplacement prévu et appuyez sur Ctrl+V, ou cliquez avec le bouton droit sur l’élément de menu du plus haut niveau qui se trouve avant le nouvel emplacement prévu et sélectionnez **Coller** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7101e-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="7101e-108">Le menu que vous avez copié est inséré avant le menu du plus haut niveau sélectionné.</span><span class="sxs-lookup"><span data-stu-id="7101e-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="7101e-109">Pour copier un menu du plus haut niveau et ses éléments de sous-menu à un emplacement déroulant</span><span class="sxs-lookup"><span data-stu-id="7101e-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="7101e-110">Cliquez sur le menu que vous voulez déplacer et appuyez sur Ctrl+C, ou cliquez avec le bouton droit sur le menu et sélectionnez **Copier** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7101e-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="7101e-111">Dans le menu du plus haut niveau de destination, cliquez sur l’élément de sous-menu qui se trouve au-dessus du nouvel emplacement prévu et appuyez sur Ctrl+V, ou cliquez avec le bouton droit sur l’élément de sous-menu qui se trouve au-dessus du nouvel emplacement prévu et sélectionnez **Coller** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7101e-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="7101e-112">Le menu que vous avez copié est inséré avant l’élément de sous-menu sélectionné.</span><span class="sxs-lookup"><span data-stu-id="7101e-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="7101e-113">Pour copier un élément de sous-menu vers un autre menu</span><span class="sxs-lookup"><span data-stu-id="7101e-113">To copy a submenu item to another menu</span></span>  
  
1.  <span data-ttu-id="7101e-114">Cliquez sur l’élément de sous-menu que vous voulez copier et appuyez sur Ctrl+C, ou cliquez avec le bouton droit sur l’élément de sous-menu et choisissez **Copier** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7101e-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="7101e-115">Cliquez sur le menu qui contiendra l’élément de sous-menu que vous coupez.</span><span class="sxs-lookup"><span data-stu-id="7101e-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3.  <span data-ttu-id="7101e-116">Cliquez sur l’élément de sous-menu qui se trouve avant le nouvel emplacement prévu et appuyez sur Ctrl+V, ou cliquez avec le bouton droit sur l’élément de sous-menu qui se trouve avant le nouvel emplacement prévu et sélectionnez **Coller** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7101e-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="7101e-117">L’élément de sous-menu que vous avez copié est inséré avant l’élément de sous-menu sélectionné.</span><span class="sxs-lookup"><span data-stu-id="7101e-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7101e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7101e-118">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="7101e-119">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="7101e-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
