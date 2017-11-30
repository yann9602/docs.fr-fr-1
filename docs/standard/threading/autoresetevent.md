---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a>AutoResetEvent
La <xref:System.Threading.AutoResetEvent> classe représente un événement de handle d’attente local qui se réinitialise automatiquement quand il est signalé, après avoir libéré un seul thread en attente. Cette classe représente un cas spécial de sa classe de base, <xref:System.Threading.EventWaitHandle>. Consultez la documentation conceptuelle de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) relative à l’utilisation et aux fonctionnalités des événements de réinitialisation automatique.  
  
 Un <xref:System.Threading.AutoResetEvent> objet est automatiquement réinitialisé à non signalé par le système après la libération d’un seul thread en attente. Si aucun thread n’attend, l’état de l’objet d’événement reste signalé. <xref:System.Threading.AutoResetEvent>correspond à un Win32 `CreateEvent` appelez, en spécifiant `false` pour la `bManualReset` argument.  
  
 Pour obtenir un exemple qui utilise <xref:System.Threading.AutoResetEvent>, consultez [analyse](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Thread](../../../docs/standard/threading/index.md)  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Descripteurs d’attente](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
