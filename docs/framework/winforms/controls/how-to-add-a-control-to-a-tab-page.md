---
title: "Comment : ajouter un contrôle à une page d'onglet"
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
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ac6e436aeeafcaa66ff0e3bec213c2316302fd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-control-to-a-tab-page"></a><span data-ttu-id="43a8a-102">Comment : ajouter un contrôle à une page d'onglet</span><span class="sxs-lookup"><span data-stu-id="43a8a-102">How to: Add a Control to a Tab Page</span></span>
<span data-ttu-id="43a8a-103">Vous pouvez utiliser Windows Forms <xref:System.Windows.Forms.TabControl> pour afficher d’autres contrôles dans une structure organisée.</span><span class="sxs-lookup"><span data-stu-id="43a8a-103">You can use the Windows Forms <xref:System.Windows.Forms.TabControl> to display other controls in an organized fashion.</span></span> <span data-ttu-id="43a8a-104">La procédure suivante montre comment ajouter un bouton vers le premier onglet. Pour plus d’informations sur l’ajout d’une icône à la partie de l’étiquette d’une page d’onglet, consultez [Comment : modifier l’apparence du contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="43a8a-104">The following procedure shows how to add a button to the first tab. For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
### <a name="to-add-a-control-programmatically"></a><span data-ttu-id="43a8a-105">Pour ajouter un contrôle par programmation</span><span class="sxs-lookup"><span data-stu-id="43a8a-105">To add a control programmatically</span></span>  
  
1.  <span data-ttu-id="43a8a-106">Utilisez le <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> méthode de la collection retournée par la <xref:System.Windows.Forms.Control.Controls%2A> propriété du <xref:System.Windows.Forms.TabPage>:</span><span class="sxs-lookup"><span data-stu-id="43a8a-106">Use the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.Control.Controls%2A> property of <xref:System.Windows.Forms.TabPage>:</span></span>  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="43a8a-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43a8a-107">See Also</span></span>  
 [<span data-ttu-id="43a8a-108">TabControl, contrôle</span><span class="sxs-lookup"><span data-stu-id="43a8a-108">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="43a8a-109">Vue d’ensemble du contrôle TabControl</span><span class="sxs-lookup"><span data-stu-id="43a8a-109">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="43a8a-110">Guide pratique pour modifier l'apparence du contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43a8a-110">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="43a8a-111">Guide pratique pour désactiver les pages d'onglets</span><span class="sxs-lookup"><span data-stu-id="43a8a-111">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="43a8a-112">Guide pratique pour ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43a8a-112">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
