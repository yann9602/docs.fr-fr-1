---
title: "AutoResetEvent | Microsoft Docs"
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
  - "threading [.NET Framework], AutoResetEvent class"
  - "AutoResetEvent class"
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# AutoResetEvent
La classe <xref:System.Threading.AutoResetEvent> représente un événement de descripteur d'attente local qui se réinitialise automatiquement lorsqu'il a été signalé, après avoir libéré un seul thread en attente.  Cette classe représente un cas spécial de sa classe de base, <xref:System.Threading.EventWaitHandle>.  Consultez la documentation conceptuelle [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) sur l'utilisation et les fonctionnalités des événements de réinitialisation automatique.  
  
 Le système redonne automatiquement l'état non signalé à un objet <xref:System.Threading.AutoResetEvent> après la libération d'un seul thread en attente.  Si aucun thread n'est en attente, l'objet événement reste à l'état signalé.  <xref:System.Threading.AutoResetEvent> correspond à un appel de Win32 `CreateEvent`, en donnant la valeur `false` à l'argument `bManualReset`.  
  
 Pour obtenir un exemple de l'utilisation de <xref:System.Threading.AutoResetEvent>, consultez [Monitor](../Topic/Monitors.md).  
  
## Voir aussi  
 <xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.Monitor>   
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Wait Handles](../Topic/Wait%20Handles.md)