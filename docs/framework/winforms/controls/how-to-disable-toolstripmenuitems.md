---
title: "Comment : désactiver des ToolStripMenuItems"
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
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0432c59979f8f595b481154f5b339e448ee66b06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="63ade-102">Comment : désactiver des ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="63ade-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="63ade-103">Vous pouvez limiter ou élargir les commandes de que l’utilisateur peut effectuer par activation et désactivation des éléments de menu en réponse aux activités de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="63ade-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="63ade-104">Éléments de menu sont activés par défaut lorsqu’ils sont créés, mais cela peut être ajusté par la <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="63ade-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="63ade-105">Vous pouvez modifier cette propriété au moment du design dans le **propriétés** fenêtre ou par programme en définissant dans le code.</span><span class="sxs-lookup"><span data-stu-id="63ade-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="63ade-106">Pour désactiver un élément de menu par programme</span><span class="sxs-lookup"><span data-stu-id="63ade-106">To disable a menu item programmatically</span></span>  
  
-   <span data-ttu-id="63ade-107">Dans la méthode où vous définissez les propriétés de l’élément de menu, ajoutez le code pour définir le <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="63ade-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="63ade-108">La désactivation de l’élément de menu de niveau supérieur ou première dans un menu masque tous les éléments de menu contenus dans le menu, mais ne désactive pas les.</span><span class="sxs-lookup"><span data-stu-id="63ade-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="63ade-109">De même, la désactivation d’un élément de menu qui comporte des éléments de sous-menu masque les éléments de sous-menu, mais ne désactive pas les.</span><span class="sxs-lookup"><span data-stu-id="63ade-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="63ade-110">Si toutes les commandes de menu ne sont pas disponibles à l’utilisateur, il est considéré comme bonne pratique de programmation à masquer et désactiver l’intégralité du menu, comme cela présente une interface utilisateur propre.</span><span class="sxs-lookup"><span data-stu-id="63ade-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="63ade-111">Masquer et désactivez le menu et chaque élément et l’élément de sous-menu du menu, de désactiver, car le masquage seul n’empêche pas l’accès à une commande de menu via une touche de raccourci.</span><span class="sxs-lookup"><span data-stu-id="63ade-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="63ade-112">Définir le <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriété d’un élément de menu de niveau supérieur pour `false` pour masquer l’intégralité du menu.</span><span class="sxs-lookup"><span data-stu-id="63ade-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63ade-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63ade-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="63ade-114">Guide pratique pour masquer des ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="63ade-114">How to: Hide ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [<span data-ttu-id="63ade-115">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="63ade-115">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
