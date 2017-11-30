---
title: "Vue d'ensemble des gestionnaires d'événements (Windows Forms)"
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
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="d1471-102">Vue d'ensemble des gestionnaires d'événements (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d1471-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="d1471-103">Un gestionnaire d’événements est une méthode qui est liée à un événement.</span><span class="sxs-lookup"><span data-stu-id="d1471-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="d1471-104">Lorsque l’événement est déclenché, le code dans le Gestionnaire d’événements est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d1471-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="d1471-105">Chaque gestionnaire d’événements fournit deux paramètres qui vous permettent de gérer l’événement correctement.</span><span class="sxs-lookup"><span data-stu-id="d1471-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="d1471-106">L’exemple suivant montre un gestionnaire d’événements pour un <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> événement.</span><span class="sxs-lookup"><span data-stu-id="d1471-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 <span data-ttu-id="d1471-107">Le premier paramètre,`sender`, fournit une référence à l’objet qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="d1471-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="d1471-108">Le deuxième paramètre, `e`, dans l’exemple ci-dessus, passe un objet spécifique à l’événement qui est géré.</span><span class="sxs-lookup"><span data-stu-id="d1471-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="d1471-109">En faisant référence à des propriétés de l’objet (et parfois ses méthodes), vous pouvez obtenir des informations telles que l’emplacement de la souris pour les événements de souris ou les données transférées dans les événements de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="d1471-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="d1471-110">En général, chaque événement produit un gestionnaire d’événements avec un type d’objet d’événement différentes pour le deuxième paramètre.</span><span class="sxs-lookup"><span data-stu-id="d1471-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="d1471-111">Certains gestionnaires d’événements, comme celles qui concernent le <xref:System.Windows.Forms.Control.MouseDown> et <xref:System.Windows.Forms.Control.MouseUp> événements, ont le même type d’objet pour le second paramètre.</span><span class="sxs-lookup"><span data-stu-id="d1471-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="d1471-112">Pour ces types d’événements, vous pouvez utiliser le même gestionnaire d’événements pour gérer les deux événements.</span><span class="sxs-lookup"><span data-stu-id="d1471-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="d1471-113">Vous pouvez également utiliser le même gestionnaire d’événements pour gérer l’événement de même pour les différents contrôles.</span><span class="sxs-lookup"><span data-stu-id="d1471-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="d1471-114">Par exemple, si vous avez un groupe de <xref:System.Windows.Forms.RadioButton> contrôles sur un formulaire, vous pouvez créer un seul gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> événement et de chaque contrôle <xref:System.Windows.Forms.Control.Click> événement lié au gestionnaire d’événements unique.</span><span class="sxs-lookup"><span data-stu-id="d1471-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="d1471-115">Pour plus d’informations, consultez [Comment : connecter plusieurs événements à un seul gestionnaire d’événements dans les Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d1471-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1471-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1471-116">See Also</span></span>  
 [<span data-ttu-id="d1471-117">Création de gestionnaires d’événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1471-117">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="d1471-118">Vue d'ensemble des événements</span><span class="sxs-lookup"><span data-stu-id="d1471-118">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)
