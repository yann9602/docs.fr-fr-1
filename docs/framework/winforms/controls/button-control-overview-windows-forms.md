---
title: "Vue d'ensemble du contrôle Button (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e04b99c9d85ae92ad4d013abc01c5b16914fe1c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="button-control-overview-windows-forms"></a><span data-ttu-id="1f805-102">Vue d'ensemble du contrôle Button (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1f805-102">Button Control Overview (Windows Forms)</span></span>
<span data-ttu-id="1f805-103">Le contrôle Windows Forms <xref:System.Windows.Forms.Button> permet à l'utilisateur d'effectuer une action en cliquant dessus.</span><span class="sxs-lookup"><span data-stu-id="1f805-103">The Windows Forms <xref:System.Windows.Forms.Button> control allows the user to click it to perform an action.</span></span> <span data-ttu-id="1f805-104">Quand le bouton est activé, il donne l'impression d'être enfoncé puis relâché.</span><span class="sxs-lookup"><span data-stu-id="1f805-104">When the button is clicked, it looks as if it is being pushed in and released.</span></span> <span data-ttu-id="1f805-105">Chaque fois que l’utilisateur clique sur un bouton, le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements est appelé.</span><span class="sxs-lookup"><span data-stu-id="1f805-105">Whenever the user clicks a button, the <xref:System.Windows.Forms.Control.Click> event handler is invoked.</span></span> <span data-ttu-id="1f805-106">Vous placez le code dans le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements pour exécuter toute action que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="1f805-106">You place code in the <xref:System.Windows.Forms.Control.Click> event handler to perform any action you choose.</span></span>  
  
 <span data-ttu-id="1f805-107">Le texte affiché sur le bouton est contenu dans le <xref:System.Windows.Forms.Control.Text%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="1f805-107">The text displayed on the button is contained in the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="1f805-108">Si votre texte dépasse la largeur du bouton, il encapsule à la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="1f805-108">If your text exceeds the width of the button, it will wrap to the next line.</span></span> <span data-ttu-id="1f805-109">Toutefois, il apparaît découpé si le contrôle ne peut pas prendre en charge sa hauteur totale.</span><span class="sxs-lookup"><span data-stu-id="1f805-109">However, it will be clipped if the control cannot accommodate its overall height.</span></span> <span data-ttu-id="1f805-110">Pour plus d’informations, consultez [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f805-110">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span> <span data-ttu-id="1f805-111">Le <xref:System.Windows.Forms.Control.Text%2A> propriété peut contenir une clé d’accès, ce qui permet à un utilisateur « sur « le contrôle en appuyant sur la touche ALT et la clé d’accès.</span><span class="sxs-lookup"><span data-stu-id="1f805-111">The <xref:System.Windows.Forms.Control.Text%2A> property can contain an access key, which allows a user to "click" the control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="1f805-112">Pour plus d’informations, consultez [Comment : créer de touches d’accès rapide pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1f805-112">For details, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span> <span data-ttu-id="1f805-113">L’apparence du texte est contrôlée par le <xref:System.Windows.Forms.Control.Font%2A> propriété et le <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="1f805-113">The appearance of the text is controlled by the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> property.</span></span>  
  
 <span data-ttu-id="1f805-114">Le <xref:System.Windows.Forms.Button> contrôle peut également afficher des images à l’aide de la <xref:System.Windows.Forms.ButtonBase.Image%2A> et <xref:System.Windows.Forms.ButtonBase.ImageList%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="1f805-114">The <xref:System.Windows.Forms.Button> control can also display images using the <xref:System.Windows.Forms.ButtonBase.Image%2A> and <xref:System.Windows.Forms.ButtonBase.ImageList%2A> properties.</span></span> <span data-ttu-id="1f805-115">Pour plus d’informations, consultez [Comment : définir l’Image affichée par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f805-115">For more information, see [How to: Set the Image Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f805-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f805-116">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="1f805-117">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f805-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="1f805-118">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f805-118">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="1f805-119">Guide pratique pour désigner un bouton Windows Forms comme bouton Accepter à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="1f805-119">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="1f805-120">Guide pratique pour désigner un bouton Windows Forms comme bouton Annuler à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="1f805-120">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="1f805-121">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="1f805-121">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
