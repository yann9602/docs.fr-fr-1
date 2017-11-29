---
title: "Événements dans les contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e568dd7fadea8af399a63aa95347f368b4e13a54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="58fbb-102">Événements dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="58fbb-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="58fbb-103">Un contrôle Windows Forms hérite plus de soixante événements de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58fbb-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="58fbb-104">Celles-ci incluent la <xref:System.Windows.Forms.Control.Paint> événement, ce qui entraîne un contrôle doit être dessiné, les événements liés à l’affichage d’une fenêtre, comme le <xref:System.Windows.Forms.Control.Resize> et <xref:System.Windows.Forms.Control.Layout> événements et les événements de souris et clavier bas niveau.</span><span class="sxs-lookup"><span data-stu-id="58fbb-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="58fbb-105">Certains événements de niveau inférieur sont synthétisés par <xref:System.Windows.Forms.Control> en événements de sémantique comme <xref:System.Windows.Forms.Control.Click> et <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="58fbb-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="58fbb-106">Pour plus d’informations sur les événements hérités, consultez <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="58fbb-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="58fbb-107">Si votre contrôle personnalisé doit remplacer des fonctionnalités d’événements héritées, remplacez la méthode `On`*EventName* plutôt que d’attacher un délégué.</span><span class="sxs-lookup"><span data-stu-id="58fbb-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="58fbb-108">Si le modèle d’événement dans le .NET Framework ne vous est pas familier, consultez la page [Déclencher des événements à partir d’un composant](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="58fbb-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58fbb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58fbb-109">See Also</span></span>  
 [<span data-ttu-id="58fbb-110">Remplacer la méthode OnPaint</span><span class="sxs-lookup"><span data-stu-id="58fbb-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [<span data-ttu-id="58fbb-111">Gestion des entrées utilisateur</span><span class="sxs-lookup"><span data-stu-id="58fbb-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [<span data-ttu-id="58fbb-112">Définition d’un événement</span><span class="sxs-lookup"><span data-stu-id="58fbb-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="58fbb-113">Événements</span><span class="sxs-lookup"><span data-stu-id="58fbb-113">Events</span></span>](../../../../docs/standard/events/index.md)
