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
ms.workload: dotnet
ms.openlocfilehash: f83c1c86539d61ab1b7539bfc92b676773188774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-copy-toolstripmenuitems"></a>Comment : copier des ToolStripMenuItems
Au moment du design, vous pouvez copier la totalité des menus du plus haut niveau et leurs éléments de sous-menu à un autre emplacement sur la <xref:System.Windows.Forms.MenuStrip>. Vous pouvez également copier des éléments de menu individuels entre des menus du plus haut niveau ou changer la position des éléments de menu dans un menu.  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a>Pour copier un menu du plus haut niveau et ses éléments de sous-menu vers un autre emplacement du plus haut niveau  
  
1.  Cliquez sur le menu que vous voulez copier et appuyez sur Ctrl+C, ou cliquez avec le bouton droit sur le menu et sélectionnez **Copier** dans le menu contextuel.  
  
2.  Cliquez sur le menu du plus haut niveau qui se trouve après le nouvel emplacement prévu et appuyez sur Ctrl+V, ou cliquez avec le bouton droit sur l’élément de menu du plus haut niveau qui se trouve avant le nouvel emplacement prévu et sélectionnez **Coller** dans le menu contextuel.  
  
     Le menu que vous avez copié est inséré avant le menu du plus haut niveau sélectionné.  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a>Pour copier un menu du plus haut niveau et ses éléments de sous-menu à un emplacement déroulant  
  
1.  Cliquez sur le menu que vous voulez déplacer et appuyez sur Ctrl+C, ou cliquez avec le bouton droit sur le menu et sélectionnez **Copier** dans le menu contextuel.  
  
2.  Dans le menu du plus haut niveau de destination, cliquez sur l’élément de sous-menu qui se trouve au-dessus du nouvel emplacement prévu et appuyez sur Ctrl+V, ou cliquez avec le bouton droit sur l’élément de sous-menu qui se trouve au-dessus du nouvel emplacement prévu et sélectionnez **Coller** dans le menu contextuel.  
  
     Le menu que vous avez copié est inséré avant l’élément de sous-menu sélectionné.  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a>Pour copier un élément de sous-menu vers un autre menu  
  
1.  Cliquez sur l’élément de sous-menu que vous voulez copier et appuyez sur Ctrl+C, ou cliquez avec le bouton droit sur l’élément de sous-menu et choisissez **Copier** dans le menu contextuel.  
  
2.  Cliquez sur le menu qui contiendra l’élément de sous-menu que vous coupez.  
  
3.  Cliquez sur l’élément de sous-menu qui se trouve avant le nouvel emplacement prévu et appuyez sur Ctrl+V, ou cliquez avec le bouton droit sur l’élément de sous-menu qui se trouve avant le nouvel emplacement prévu et sélectionnez **Coller** dans le menu contextuel.  
  
     L’élément de sous-menu que vous avez copié est inséré avant l’élément de sous-menu sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
