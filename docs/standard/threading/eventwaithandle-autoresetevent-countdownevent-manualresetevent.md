---
title: "EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "wait handles"
  - "threading [.NET Framework], EventWaitHandle class"
  - "event wait handles [.NET Framework]"
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
Les handles d'attente d'événement permettent aux threads de synchroniser des activités en échangeant des signaux et en attendant de recevoir ces signaux.  Ces événements de synchronisation sont basés sur des handles d'attente Win32 et peuvent être subdivisés en deux types : ceux dont la réinitialisation est automatique et ceux qui sont réinitialisés manuellement.  
  
 Les handles d'attente d'événement sont utiles dans de nombreux scénarios de synchronisation identiques à ceux de la classe <xref:System.Threading.Monitor>.  Les handles d'attente d'événement sont souvent plus faciles d'utiliser que les méthodes <xref:System.Threading.Monitor.Wait%2A?displayProperty=fullName> et <xref:System.Threading.Monitor.Pulse%2A?displayProperty=fullName>, et ils offrent davantage de contrôle sur la signalisation.  Les handles d'attente d'événement nommés peuvent également être utilisés pour synchroniser des activités entre des processus et domaines d'application tandis que les moniteurs sont réservés à un usage local, au sein d'un domaine d'application.  
  
## Dans cette section  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 La classe <xref:System.Threading.EventWaitHandle> peut représenter des événements de réinitialisation automatique ou manuelle et des événements locaux ou des événements système nommés.  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 La classe <xref:System.Threading.AutoResetEvent> dérive de <xref:System.Threading.EventWaitHandle> et représente un événement local qui se réinitialise automatiquement.  
  
 [ManualResetEvent and ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 La classe <xref:System.Threading.ManualResetEvent> dérive de <xref:System.Threading.EventWaitHandle> et représente un événement local qui doit être réinitialisé manuellement.  La classe <xref:System.Threading.ManualResetEventSlim> est une version simplifiée et plus rapide qui peut être utilisée pour des événements au sein du même processus.  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 La classe <xref:System.Threading.CountdownEvent> fournit un moyen simple d'implémenter le modèle de parallélisme bifurcation\/jointure dans du code qui utilise des handles d'attente.  
  
## Rubriques connexes  
 [Wait Handles](../Topic/Wait%20Handles.md)  
 La classe <xref:System.Threading.WaitHandle> est la classe de base des classes <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore> et <xref:System.Threading.Mutex>.  Elle contient des méthodes statiques telles que <xref:System.Threading.WaitHandle.SignalAndWait%2A> et <xref:System.Threading.WaitHandle.WaitAll%2A>, lesquelles sont utiles lorsque vous utilisez tous les types de handles d'attente.  
  
## Voir aussi  
 <xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading.WaitHandle>   
 <xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent>   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)