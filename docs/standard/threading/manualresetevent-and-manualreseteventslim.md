---
title: ManualResetEvent et ManualResetEventSlim
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f663dd17b063f77e2f9ce6bd4bbd0f8859ba4116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent et ManualResetEventSlim
La <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> classe représente un événement de handle d’attente local qui doit être réinitialisé manuellement une fois qu’il est signalé. Cette classe représente un cas spécial de sa classe de base, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>. Consultez la documentation conceptuelle de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) relative à l’utilisation et aux fonctionnalités des événements de réinitialisation manuelle.  
  
 A <xref:System.Threading.ManualResetEvent> objet reste signalé jusqu'à ce que son <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> méthode est appelée. Lorsque l’état de l’objet est signalé, un nombre indéterminé de threads en attente, ou de threads attendant l’événement une fois celui-ci signalé, peuvent être libérés. <xref:System.Threading.ManualResetEvent>correspond à un Win32 `CreateEvent` appelez, en spécifiant `true` pour la `bManualReset` argument.  
  
 Dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez utiliser la <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> classe pour de meilleures performances lorsque les temps d’attente sont supposés être très courts et lorsque l’événement ne dépasse pas une limite de processus. <xref:System.Threading.ManualResetEventSlim>utilise la rotation intensive pendant une courte période en attendant que l’événement soit signalé. Lorsque les temps d’attente sont courts, la rotation peut s’avérer beaucoup moins coûteuse que les descripteurs d’attente. Toutefois, si l’événement n’est pas signalé dans un certain temps, <xref:System.Threading.ManualResetEventSlim> a recours à une attente de handle d’événement régulier.  
  
## <a name="see-also"></a>Voir aussi  
 [Thread](../../../docs/standard/threading/index.md)  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Descripteurs d’attente](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Semaphore et SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
