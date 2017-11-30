---
title: "Comment : créer des gestionnaires d'événements pour les Windows Forms au moment de l'exécution"
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
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53664bcf8c776338399297687a16ec430bca128b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="d11eb-102">Comment : créer des gestionnaires d'événements pour les Windows Forms au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="d11eb-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>
<span data-ttu-id="d11eb-103">Outre la création d’événements à l’aide du Concepteur Windows Forms, vous pouvez créer un gestionnaire d’événements au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d11eb-103">In addition to creating events using the Windows Forms Designer, you can also create an event handler at run time.</span></span> <span data-ttu-id="d11eb-104">Cette action vous permet de connecter des gestionnaires d’événements en fonction de conditions spécifiées dans le code lors de l’exécution au lieu de les connecter au premier démarrage du programme.</span><span class="sxs-lookup"><span data-stu-id="d11eb-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>  
  
### <a name="to-create-an-event-handler-at-run-time"></a><span data-ttu-id="d11eb-105">Pour créer un gestionnaire d’événements au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="d11eb-105">To create an event handler at run time</span></span>  
  
1.  <span data-ttu-id="d11eb-106">Ouvrez le formulaire auquel vous souhaitez ajouter un gestionnaire d’événements dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="d11eb-106">Open the form in the Code Editor that you want to add an event handler to.</span></span>  
  
2.  <span data-ttu-id="d11eb-107">Ajoutez une méthode à votre formulaire avec la signature de méthode pour l’événement que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="d11eb-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>  
  
     <span data-ttu-id="d11eb-108">Par exemple, si vous gérez le <xref:System.Windows.Forms.Control.Click> événements d’un <xref:System.Windows.Forms.Button> (contrôle), vous devez créer une méthode telle que la suivante :</span><span class="sxs-lookup"><span data-stu-id="d11eb-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)  
       ' Add event handler code here.  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
    // Add event handler code here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          // Add event handler code here.  
       }  
    ```  
  
3.  <span data-ttu-id="d11eb-109">Ajoutez le code au gestionnaire d’événements en fonction de votre application.</span><span class="sxs-lookup"><span data-stu-id="d11eb-109">Add code to the event handler as appropriate to your application.</span></span>  
  
4.  <span data-ttu-id="d11eb-110">Déterminez le formulaire ou le contrôle pour lequel vous souhaitez créer un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d11eb-110">Determine which form or control you want to create an event handler for.</span></span>  
  
5.  <span data-ttu-id="d11eb-111">Dans une méthode de classe de votre formulaire, ajoutez le code qui spécifie au gestionnaire d’événements de gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="d11eb-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="d11eb-112">Par exemple, le code suivant spécifie le Gestionnaire d’événements `button1_Click` gère la <xref:System.Windows.Forms.Control.Click> événement d’un <xref:System.Windows.Forms.Button> contrôle :</span><span class="sxs-lookup"><span data-stu-id="d11eb-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="d11eb-113">Le <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> méthode présentée dans le code Visual Basic ci-dessus établit un gestionnaire d’événements click du bouton.</span><span class="sxs-lookup"><span data-stu-id="d11eb-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d11eb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d11eb-114">See Also</span></span>  
 [<span data-ttu-id="d11eb-115">Création de gestionnaires d’événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d11eb-115">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="d11eb-116">Vue d'ensemble des gestionnaires d'événements</span><span class="sxs-lookup"><span data-stu-id="d11eb-116">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 [<span data-ttu-id="d11eb-117">Dépannage des gestionnaires d’événements hérités en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d11eb-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
