---
title: "Comment : détecter lorsque le pointeur de la souris est sur un ToolStripItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 633b92bf6da837b3727001c621548fa58b230102
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="81c89-102">Comment : détecter lorsque le pointeur de la souris est sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="81c89-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="81c89-103">Utilisez la procédure suivante pour détecter lorsque le pointeur de la souris est sur un <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="81c89-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="81c89-104">Détecter lorsque le pointeur est sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="81c89-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
-   <span data-ttu-id="81c89-105">Utilisez le <xref:System.Windows.Forms.ToolStripItem.Selected%2A> propriété des éléments dans laquelle <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> est `true`.</span><span class="sxs-lookup"><span data-stu-id="81c89-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="81c89-106">Cela vous empêchera d’avoir à synchroniser le <xref:System.Windows.Forms.ToolStripItem.MouseEnter> et <xref:System.Windows.Forms.ToolStripItem.MouseLeave> les événements.</span><span class="sxs-lookup"><span data-stu-id="81c89-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c89-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81c89-107">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>  
 [<span data-ttu-id="81c89-108">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="81c89-108">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
