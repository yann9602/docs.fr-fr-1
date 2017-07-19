---
title: "ManualResetEvent and ManualResetEventSlim | Microsoft Docs"
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
  - "threading [.NET Framework], ManualResetEvent class"
  - "ManualResetEvent class, about ManualResetEvent class"
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# ManualResetEvent and ManualResetEventSlim
La classe <xref:System.Threading.ManualResetEvent?displayProperty=fullName> représente un événement du handle d'attente local qui doit être réinitialisé manuellement une fois signalé.  Cette classe représente un cas spécifique de la classe de base correspondante \(<xref:System.Threading.EventWaitHandle?displayProperty=fullName>\).  Consultez la documentation conceptuelle [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) pour plus d'informations sur l'utilisation et les fonctions des événements à réinitialisation manuelle.  
  
 Un objet <xref:System.Threading.ManualResetEvent> reste signalé jusqu'à ce que sa méthode <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=fullName> soit appelée.  Vous pouvez libérer n'importe quel nombre de threads en attente \(ou de threads en attente une fois l'événement signalé\) pendant que l'état de l'objet est Signalé.  <xref:System.Threading.ManualResetEvent> correspond à un appel de Win32 `CreateEvent`, en donnant la valeur `true` à l'argument `bManualReset`.  
  
 Avec le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] vous pouvez utiliser la classe <xref:System.Threading.ManualResetEventSlim?displayProperty=fullName> pour de meilleures performances lorsque les temps d'attente sont supposés être très courts et, lorsque l'événement ne dépasse pas une limite de processus.  <xref:System.Threading.ManualResetEventSlim> utilise une rotation intensive pendant une courte période pendant qu'il attend l'événement soit signalé.  Lorsque les temps d'attente sont courts, la rotation peut être beaucoup moins coûteuse que l'utilisation de handles d'attente.  Toutefois, si l'événement n'est pas signalé avant un temps donné, <xref:System.Threading.ManualResetEventSlim> a recours à une attente de descripteur d'événement normale.  
  
## Voir aussi  
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Wait Handles](../Topic/Wait%20Handles.md)   
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)   
 [SpinWait](../../../docs/standard/threading/spinwait.md)   
 [Semaphore and SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)