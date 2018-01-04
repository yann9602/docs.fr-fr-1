---
title: "Entrée d’utilisateur dans une application Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60135c09f63bd98f753e151c515938cbf13e70ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="user-input-in-a-windows-forms-application"></a>Entrée d’utilisateur dans une application Windows Forms
Dans les Windows Forms, l’entrée d’utilisateur est envoyée aux applications sous la forme de messages Windows. Une série de méthodes substituables traite ces messages au niveau de l’application, du formulaire et niveau de contrôle. Lorsque ces méthodes reçoivent les messages de clavier et souris, ils déclenchent des événements qui peuvent être gérés pour obtenir des informations sur la souris ou du clavier d’entrée. Dans de nombreux cas, les applications Windows Forms seront en mesure de traiter toutes les entrées utilisateur simplement en gérant ces événements. Dans d’autres cas, une application devrez peut-être remplacer une des méthodes qui traitent les messages afin d’intercepter un message particulier avant qu’il est reçu par l’application, un formulaire ou un contrôle.  
  
## <a name="mouse-and-keyboard-events"></a>Événements de souris et clavier  
 Tous les contrôles Windows Forms héritent d’un ensemble d’événements liés à la souris et clavier. Par exemple, un contrôle peut gérer le <xref:System.Windows.Forms.Control.KeyPress> événement afin de déterminer le code de caractère d’une clé qui a été enfoncée, ou un contrôle peut gérer le <xref:System.Windows.Forms.Control.MouseClick> événement pour déterminer l’emplacement de la souris, cliquez sur. Pour plus d’informations sur les événements de souris et de clavier, consultez [à l’aide des événements de clavier](../../../docs/framework/winforms/using-keyboard-events.md) et [les événements de souris dans les Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Méthodes qui traitent les Messages d’entrée d’utilisateur  
 Formulaires et les contrôles ont accès à la <xref:System.Windows.Forms.IMessageFilter> interface et un jeu de méthodes substituables qui traitent les messages Windows à différents points dans la file d’attente. Ces méthodes ont tous un <xref:System.Windows.Forms.Message> paramètre, qui encapsule les détails de bas niveau des messages Windows. Vous pouvez implémenter ou substituer ces méthodes pour examiner le message, puis consommer le message ou la passer au consommateur suivant dans la file d’attente. Le tableau suivant présente les méthodes qui traitent tous les messages Windows dans les Windows Forms.  
  
|Méthode|Notes|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Cette méthode intercepte en file d’attente des messages Windows (également appelé validées) au niveau de l’application.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Cette méthode intercepte les messages Windows au niveau du formulaire et de contrôle avant qu’ils ont été traités.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Cette méthode traite les messages Windows au niveau du formulaire et de contrôle.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Cette méthode effectue le traitement par défaut des messages Windows au niveau du formulaire et de contrôle. Cela fournit les fonctionnalités minimales d’une fenêtre.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Cette méthode intercepte les messages au niveau du formulaire et de contrôle, une fois qu’ils ont été traités. Le <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> bit de style doit être définie pour cette méthode à appeler.|  
  
 Les messages de clavier et souris sont également traités par un jeu supplémentaire de méthodes substituables qui sont spécifiques à ces types de messages. Pour plus d’informations, consultez [fonctionnement des entrées au clavier](../../../docs/framework/winforms/how-keyboard-input-works.md) et [souris entrée fonctionnement dans les Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Entrées d’utilisateur dans les Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 [Entrée au clavier dans une application Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Entrée de la souris dans une application Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
