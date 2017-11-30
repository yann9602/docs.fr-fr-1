---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
Les handles d’attente d’événements permettent aux threads de synchroniser les activités en se signalant et en attendant les signaux des uns et des autres. Ces événements de synchronisation s’appuient sur des handles d’attente Win32 et se divisent en deux types : ceux qui se réinitialisent automatiquement et ceux qui sont réinitialisés manuellement.  
  
 Handles d’attente d’événement sont utiles dans la plupart des scénarios de synchronisation même comme le <xref:System.Threading.Monitor> classe. Handles d’attente d’événement sont souvent plus faciles à utiliser que les <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> et <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> méthodes et ils offrent davantage de contrôle sur la signalisation. Les handles d’attente d’événements nommés peuvent également servir à synchroniser les activités entre les différents processus et domaines d’application, tandis que les moniteurs sont liés localement à un domaine d’application.  
  
## <a name="in-this-section"></a>Dans cette section  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 La <xref:System.Threading.EventWaitHandle> classe peut représenter soit automatique ou manuel réinitialiser des événements et des événements locaux ou des événements de système nommés.  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 Le <xref:System.Threading.AutoResetEvent> dérive de la classe <xref:System.Threading.EventWaitHandle> et représente un événement local qui se réinitialise automatiquement.  
  
 [ManualResetEvent and ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 Le <xref:System.Threading.ManualResetEvent> dérive de la classe <xref:System.Threading.EventWaitHandle> et représente un événement local qui doit être réinitialisé manuellement. La <xref:System.Threading.ManualResetEventSlim> classe est une version légère et plus rapide, qui peut être utilisée pour les événements dans le même processus.  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 La <xref:System.Threading.CountdownEvent> classe fournit un moyen simple d’implémenter des modèles de parallélisme de bifurcation/jointure dans le code qui utilise les handles d’attente.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Descripteurs d’attente](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 Le <xref:System.Threading.WaitHandle> est la classe de base pour le <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, et <xref:System.Threading.Mutex> classes. Il contient des méthodes statiques telles que <xref:System.Threading.WaitHandle.SignalAndWait%2A> et <xref:System.Threading.WaitHandle.WaitAll%2A> qui sont utiles lorsque vous travaillez avec tous les types de handles d’attente.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Éléments fondamentaux du threading managé](../../../docs/standard/threading/managed-threading-basics.md)
