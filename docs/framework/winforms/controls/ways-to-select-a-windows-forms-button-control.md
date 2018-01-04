---
title: "Méthodes de sélection du contrôle Button Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b6fa31b89b8fbe50077933cf04aa3c17db86438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="55940-102">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="55940-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="55940-103">Un bouton Windows Forms peut être sélectionné comme suit :</span><span class="sxs-lookup"><span data-stu-id="55940-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
-   <span data-ttu-id="55940-104">Utilisez la souris pour cliquer sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="55940-104">Use a mouse to click the button.</span></span>  
  
-   <span data-ttu-id="55940-105">Appel du bouton <xref:System.Windows.Forms.Control.Click> événement dans le code.</span><span class="sxs-lookup"><span data-stu-id="55940-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
-   <span data-ttu-id="55940-106">Déplacer le focus sur le bouton en appuyant sur la touche TAB, puis choisissez le bouton en appuyant sur la touche espace ou entrée.</span><span class="sxs-lookup"><span data-stu-id="55940-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
-   <span data-ttu-id="55940-107">Appuyez sur la touche d’accès rapide (ALT + la lettre soulignée) du bouton.</span><span class="sxs-lookup"><span data-stu-id="55940-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="55940-108">Pour plus d’informations sur les touches d’accès rapide, consultez [Comment : créer de touches d’accès rapide pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="55940-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
-   <span data-ttu-id="55940-109">Si le bouton est le bouton « accepter » du formulaire, en appuyant sur entrée choisit le bouton, même si un autre contrôle a le focus, sauf si ce contrôle est un autre bouton, une zone de texte multiligne ou un contrôle personnalisé qui intercepte la touche ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="55940-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
-   <span data-ttu-id="55940-110">Si le bouton est le bouton « cancel » de l’écran, en appuyant sur ÉCHAP choisit le bouton, même si un autre contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="55940-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
-   <span data-ttu-id="55940-111">Appelez le <xref:System.Windows.Forms.Button.PerformClick%2A> (méthode) pour sélectionner le bouton par programme.</span><span class="sxs-lookup"><span data-stu-id="55940-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55940-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55940-112">See Also</span></span>  
 [<span data-ttu-id="55940-113">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="55940-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="55940-114">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="55940-114">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="55940-115">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="55940-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
