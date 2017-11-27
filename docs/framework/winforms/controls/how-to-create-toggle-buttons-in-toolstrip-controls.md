---
title: "Comment : créer des boutons bascule dans les contrôles ToolStrip"
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
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8529637db7bc4cca011d0992b257d5b8ce9aaff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="25f7a-102">Comment : créer des boutons bascule dans les contrôles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="25f7a-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="25f7a-103">Lorsqu’un utilisateur clique sur un bouton bascule, il apparaît enfoncé et conserve cet aspect jusqu'à ce que l’utilisateur clique sur le bouton Nouveau.</span><span class="sxs-lookup"><span data-stu-id="25f7a-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="25f7a-104">Pour créer un ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="25f7a-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="25f7a-105">Utiliser un code tel que l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="25f7a-105">Use code such as the following code example.</span></span> <span data-ttu-id="25f7a-106">Ce code suppose que votre formulaire contienne un <xref:System.Windows.Forms.ToolStrip> contrôle et que son <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contient un <xref:System.Windows.Forms.ToolStripButton> appelée `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="25f7a-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="25f7a-107">Il suppose également que vous disposez d’un gestionnaire d’événements appelé `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="25f7a-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="25f7a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25f7a-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripButton>  
 [<span data-ttu-id="25f7a-109">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="25f7a-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
