---
title: CountdownEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f953f6477abf1f4e0d6aaf79e67005172ff1144
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>est une primitive de synchronisation qui débloque ses threads en attente après que qu’elle a été signalé un certain nombre de fois. <xref:System.Threading.CountdownEvent>est conçu pour les scénarios dans lesquels vous utiliseriez à utiliser un <xref:System.Threading.ManualResetEvent> ou <xref:System.Threading.ManualResetEventSlim> et de décrémentation manuellement une variable avant de signaler l’événement. Par exemple, dans un scénario de bifurcation/jointure, vous pouvez simplement créer un <xref:System.Threading.CountdownEvent> qui a un nombre de signal de 5, puis démarrer cinq éléments de travail sur le thread de pool et ont chaque élément de travail appelle <xref:System.Threading.CountdownEvent.Signal%2A> lorsqu’il est terminé. Chaque appel à <xref:System.Threading.CountdownEvent.Signal%2A> décrémente le nombre de signal par 1. Sur le thread principal, l’appel à <xref:System.Threading.CountdownEvent.Wait%2A> se bloque jusqu'à ce que le nombre de signal est égale à zéro.  
  
> [!NOTE]
>  Pour le code qui n’a pas d’interagir avec les API de synchronisation .NET Framework héritées, envisagez d’utiliser <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objets ou <xref:System.Threading.Tasks.Parallel.Invoke%2A> méthode pour une approche plus facile pour exprimer le parallélisme de bifurcation-jointure.  
  
 <xref:System.Threading.CountdownEvent>présente les fonctionnalités supplémentaires suivantes :  
  
-   L’opération d’attente peut être annulée à l’aide des jetons d’annulation.  
  
-   Son nombre de signal peut être incrémenté une fois que l’instance est créée.  
  
-   Instances peuvent être réutilisées après <xref:System.Threading.CountdownEvent.Wait%2A> a retourné en appelant le <xref:System.Threading.CountdownEvent.Reset%2A> (méthode).  
  
-   Les instances exposent un <xref:System.Threading.WaitHandle> pour l’intégration avec d’autres API de synchronisation .NET Framework tels que <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Utilisation de base  
 L’exemple suivant montre comment utiliser un <xref:System.Threading.CountdownEvent> avec <xref:System.Threading.ThreadPool> des éléments de travail.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent avec annulation  
 L’exemple suivant montre comment annuler l’opération d’attente sur <xref:System.Threading.CountdownEvent> à l’aide d’un jeton d’annulation. Le modèle de base suit le modèle pour l’annulation unifiée, introduite dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Pour plus d’informations, consultez [l’annulation dans les Threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Notez que l’opération d’attente n’annule pas les threads qui le signalent. En règle générale, l’annulation est appliquée à une opération logique, et qui peut inclure l’attente sur l’événement, ainsi que tous les éléments de travail que l’attente est en cours de synchronisation. Dans cet exemple, chaque élément de travail est passé à une copie de la même jeton d’annulation afin qu’il puisse répondre à la demande d’annulation.  
  
## <a name="see-also"></a>Voir aussi  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
