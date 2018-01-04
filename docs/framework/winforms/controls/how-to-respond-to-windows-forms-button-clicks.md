---
title: "Comment : répondre à un clic du contrôle Button Windows Forms"
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
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28b0467c8b589882fe5afd7e884d0de55d8ca564
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="f6029-102">Comment : répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6029-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="f6029-103">L’utilisation de base des Windows Forms <xref:System.Windows.Forms.Button> contrôle consiste à exécuter du code lorsque le bouton est activé.</span><span class="sxs-lookup"><span data-stu-id="f6029-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="f6029-104">En cliquant sur un <xref:System.Windows.Forms.Button> contrôle génère également un nombre d’événements, tels que les <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, et <xref:System.Windows.Forms.Control.MouseUp> événements.</span><span class="sxs-lookup"><span data-stu-id="f6029-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="f6029-105">Si vous souhaitez attacher des gestionnaires d’événements pour ces événements connexes, veillez à ce que leurs actions ne sont pas en conflit.</span><span class="sxs-lookup"><span data-stu-id="f6029-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="f6029-106">Par exemple, si vous cliquez sur le bouton efface les informations que l’utilisateur a tapé dans une zone de texte, suspendant le pointeur de la souris sur le bouton ne doit pas afficher une info-bulle contenant ces informations inexistante pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="f6029-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="f6029-107">Si l’utilisateur tente de double-cliquer sur le <xref:System.Windows.Forms.Button> (contrôle), chaque clic sera traité séparément ; autrement dit, le contrôle ne prend pas en charge l’événement de double-clic.</span><span class="sxs-lookup"><span data-stu-id="f6029-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="f6029-108">Pour répondre à un clic de bouton</span><span class="sxs-lookup"><span data-stu-id="f6029-108">To respond to a button click</span></span>  
  
-   <span data-ttu-id="f6029-109">Dans du bouton `Click` <xref:System.EventHandler> écrire le code à exécuter.</span><span class="sxs-lookup"><span data-stu-id="f6029-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="f6029-110">`Button1_Click`doit être lié au contrôle.</span><span class="sxs-lookup"><span data-stu-id="f6029-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="f6029-111">Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements à exécuter pour les Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f6029-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f6029-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6029-112">See Also</span></span>  
 [<span data-ttu-id="f6029-113">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="f6029-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="f6029-114">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6029-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="f6029-115">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="f6029-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
