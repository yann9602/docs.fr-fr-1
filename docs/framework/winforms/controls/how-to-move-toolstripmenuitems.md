---
title: "Comment : déplacer des ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 342eeeb2d156488605f244da0112869a371dfa97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="899de-102">Comment : déplacer des ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="899de-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="899de-103">Au moment du design, vous pouvez déplacer l’intégralité de menus de niveau supérieur et leurs éléments de menu à un autre emplacement le <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="899de-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="899de-104">Vous pouvez également déplacer des éléments de menu individuels entre des menus de niveau supérieur ou modifier la position des éléments de menu d’un menu.</span><span class="sxs-lookup"><span data-stu-id="899de-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="899de-105">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="899de-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="899de-106">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="899de-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="899de-107">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="899de-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="899de-108">Pour déplacer un menu de niveau supérieur et ses éléments de menu à un autre emplacement de niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="899de-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="899de-109">Cliquez et maintenez le bouton gauche de la souris sur le menu que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="899de-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="899de-110">Faites glisser le point d’insertion dans le menu de niveau supérieur qui se trouve avant le nouvel emplacement prévu et relâchez le bouton gauche de la souris.</span><span class="sxs-lookup"><span data-stu-id="899de-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="899de-111">Le menu sélectionné se déplace vers la droite du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="899de-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="899de-112">Pour déplacer un menu de niveau supérieur et ses éléments de menu à un emplacement de la liste déroulante</span><span class="sxs-lookup"><span data-stu-id="899de-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="899de-113">Cliquez sur le menu que vous souhaitez déplacer et appuyez sur CTRL + X, ou le menu contextuel et sélectionnez **couper** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="899de-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="899de-114">Dans le menu de niveau supérieur de destination, cliquez sur l’élément de menu au-dessus du nouvel emplacement prévu et appuyez sur CTRL + V, ou cliquez sur l’élément de menu au-dessus du nouvel emplacement prévu et sélectionnez **coller** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="899de-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="899de-115">Le menu que vous coupez est inséré après l’élément de menu sélectionné.</span><span class="sxs-lookup"><span data-stu-id="899de-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="899de-116">Pour déplacer un élément de menu dans un menu à l’aide de l’éditeur de collections d’éléments</span><span class="sxs-lookup"><span data-stu-id="899de-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="899de-117">Cliquez sur le menu qui contient l’élément de menu que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="899de-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="899de-118">Dans le menu contextuel, choisissez **modifier les DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="899de-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="899de-119">Dans le **éditeur de collections Items**, cliquez sur l’élément de menu que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="899de-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="899de-120">Cliquez sur les touches de direction haut et bas pour déplacer l’élément de menu dans le menu.</span><span class="sxs-lookup"><span data-stu-id="899de-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="899de-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="899de-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="899de-122">Pour déplacer un élément de menu d’un menu à l’aide du clavier</span><span class="sxs-lookup"><span data-stu-id="899de-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="899de-123">Maintenez la touche ALT enfoncée.</span><span class="sxs-lookup"><span data-stu-id="899de-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="899de-124">Cliquez et maintenez le bouton gauche de la souris sur l’élément de menu que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="899de-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="899de-125">Faites glisser l’élément de menu vers le nouvel emplacement et relâchez le bouton gauche de la souris.</span><span class="sxs-lookup"><span data-stu-id="899de-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="899de-126">Pour déplacer un élément de menu à un autre menu</span><span class="sxs-lookup"><span data-stu-id="899de-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="899de-127">Cliquez sur l’élément de menu que vous souhaitez déplacer et appuyez sur CTRL + X, ou cliquez sur l’élément de menu et choisissez **couper** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="899de-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="899de-128">Cliquez sur le menu qui contiendra l’élément de menu que vous coupez.</span><span class="sxs-lookup"><span data-stu-id="899de-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="899de-129">Cliquez sur l’élément de menu qui se trouve avant le nouvel emplacement prévu et appuyez sur CTRL + V ou cliquez sur l’élément de menu qui se trouve avant le nouvel emplacement prévu et sélectionnez **coller** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="899de-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="899de-130">L’élément de menu que vous coupez est inséré après l’élément de menu sélectionné.</span><span class="sxs-lookup"><span data-stu-id="899de-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="899de-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="899de-131">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="899de-132">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="899de-132">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
