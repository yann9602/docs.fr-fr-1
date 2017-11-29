---
title: "Définition d'un événement dans les contrôles Windows Forms"
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
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 592efefecb0428f87e5ac612c8fb162aa2fe85dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="81840-102">Définition d'un événement dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="81840-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="81840-103">Pour plus d’informations sur la définition d’événements personnalisés, consultez [événements](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="81840-103">For details about defining custom events, see [Events](../../../../docs/standard/events/index.md).</span></span> <span data-ttu-id="81840-104">Si vous définissez un événement qui ne comporte pas de données associées, utilisez le type de base des données d'événement <xref:System.EventArgs>, puis utilisez <xref:System.EventHandler> en tant que délégué d'événement.</span><span class="sxs-lookup"><span data-stu-id="81840-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="81840-105">Il reste plus qu’à définir un membre d’événement et un document protégé `On` *EventName* méthode qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="81840-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="81840-106">Le fragment de code suivant montre comment le contrôle personnalisé `FlashTrackBar` définit l'événement personnalisé `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="81840-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="81840-107">Pour obtenir le code complet pour le `FlashTrackBar` exemples, consultez la [Comment : créer un Windows Forms que montre progression du contrôle](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="81840-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class FlashTrackBar  
   Inherits Control  
  
   ' The event does not have any data, so EventHandler is adequate   
   ' as the event delegate.          
   ' Define the event member using the event keyword.  
   ' In this case, for efficiency, the event is defined   
   ' using the event property construct.  
   Public Event ValueChanged As EventHandler  
   ' The protected method that raises the ValueChanged   
   ' event when the value has actually   
   ' changed. Derived controls can override this method.    
   Protected Overridable Sub OnValueChanged(e As EventArgs)  
      RaiseEvent ValueChanged(Me, e)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class FlashTrackBar : Control {  
   // The event does not have any data, so EventHandler is adequate   
   // as the event delegate.  
   private EventHandler onValueChanged;  
   // Define the event member using the event keyword.  
   // In this case, for efficiency, the event is defined   
   // using the event property construct.  
   public event EventHandler ValueChanged {  
            add {  
                onValueChanged += value;  
            }  
            remove {  
                onValueChanged -= value;  
            }  
        }  
   // The protected method that raises the ValueChanged  
   // event when the value has actually   
   // changed. Derived controls can override this method.    
   protected virtual void OnValueChanged(EventArgs e) {  
      if (ValueChanged != null) {  
         ValueChanged(this, e);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="81840-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81840-108">See Also</span></span>  
 [<span data-ttu-id="81840-109">Événements dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="81840-109">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="81840-110">Événements</span><span class="sxs-lookup"><span data-stu-id="81840-110">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="81840-111">Événements</span><span class="sxs-lookup"><span data-stu-id="81840-111">Events</span></span>](../../../../docs/standard/events/index.md)
