---
title: "Comment : désigner un contrôle Button Windows Forms en tant que bouton Annuler"
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
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3f61828b4c8b65ae984685610d6d8609953376a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="76ee0-102">Comment : désigner un contrôle Button Windows Forms en tant que bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="76ee0-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="76ee0-103">Sur un Windows Form, vous pouvez désigner un <xref:System.Windows.Forms.Button> contrôle soit le bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="76ee0-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="76ee0-104">Un bouton cancel chaque fois que l’utilisateur appuie sur la touche ÉCHAP, quels que soient les autres contrôles du formulaire a le focus.</span><span class="sxs-lookup"><span data-stu-id="76ee0-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="76ee0-105">Ce bouton est généralement programmé pour permettre à l’utilisateur de quitter rapidement une opération sans valider aucune action.</span><span class="sxs-lookup"><span data-stu-id="76ee0-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="76ee0-106">Pour désigner le bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="76ee0-106">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="76ee0-107">Valeur du formulaire <xref:System.Windows.Forms.Form.CancelButton%2A> propriété approprié <xref:System.Windows.Forms.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="76ee0-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="76ee0-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76ee0-108">See Also</span></span>  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [<span data-ttu-id="76ee0-109">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="76ee0-109">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="76ee0-110">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="76ee0-110">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="76ee0-111">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="76ee0-111">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="76ee0-112">Guide pratique pour désigner un contrôle Button Windows Forms comme bouton Accepter</span><span class="sxs-lookup"><span data-stu-id="76ee0-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [<span data-ttu-id="76ee0-113">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="76ee0-113">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
