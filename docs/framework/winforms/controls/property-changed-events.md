---
title: "Événements de modification de propriété"
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
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7685891e99f1dcb2ca9e515c7dc6d7730ff0b2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="property-changed-events"></a><span data-ttu-id="f7df8-102">Événements de modification de propriété</span><span class="sxs-lookup"><span data-stu-id="f7df8-102">Property-Changed Events</span></span>
<span data-ttu-id="f7df8-103">Si vous souhaitez que votre contrôle envoie des notifications lorsqu’une propriété nommée *PropertyName* change, définissez un événement nommé *PropertyName* `Changed` et une méthode nommée `On` *PropertyName* `Changed` qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="f7df8-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="f7df8-104">La convention d’affectation de noms dans les Windows Forms consiste à ajouter le mot *Changed* au nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f7df8-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="f7df8-105">Le type de délégué d’événement associé pour les événements de modification de propriété est <xref:System.EventHandler>, et le type de données d’événement est <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="f7df8-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="f7df8-106">La classe de base <xref:System.Windows.Forms.Control> définit de nombreux événements de modification de propriété, telle que <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>et d’autres.</span><span class="sxs-lookup"><span data-stu-id="f7df8-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="f7df8-107">Pour des informations générales sur les événements, consultez [événements](../../../../docs/standard/events/index.md) et [événements dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f7df8-107">For background information about events, see [Events](../../../../docs/standard/events/index.md) and [Events in Windows Forms Controls](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="f7df8-108">Événements de modification de propriété sont utiles car ils permettent aux consommateurs d’un contrôle attacher des gestionnaires d’événements qui répondent à la modification.</span><span class="sxs-lookup"><span data-stu-id="f7df8-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="f7df8-109">Si votre contrôle doit répondre à un événement de modification de propriété qu’il déclenche, substituez correspondant `On` *PropertyName* `Changed` méthode au lieu d’attacher un délégué à l’événement.</span><span class="sxs-lookup"><span data-stu-id="f7df8-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="f7df8-110">En général, un contrôle répond à un événement de modification de propriété en mettant à jour d’autres propriétés ou en être redessiné tout ou partie de sa surface de dessin.</span><span class="sxs-lookup"><span data-stu-id="f7df8-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="f7df8-111">L’exemple suivant montre comment la `FlashTrackBar` contrôle personnalisé répond à certains événements de modification de propriété qu’il hérite de <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="f7df8-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="f7df8-112">Pour obtenir un exemple complet, consultez [Comment : créer un Windows Forms que montre progression du contrôle](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="f7df8-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f7df8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7df8-113">See Also</span></span>  
 [<span data-ttu-id="f7df8-114">Événements</span><span class="sxs-lookup"><span data-stu-id="f7df8-114">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="f7df8-115">Événements dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7df8-115">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="f7df8-116">Propriétés dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7df8-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
