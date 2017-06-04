---
title: "CountdownEvent | Microsoft Docs"
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
  - "synchronization primitives, CountdownEvent"
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=fullName> est une primitive de synchronisation qui débloque ses threads en attente après qu'il a été signalé un certain nombre de fois.  <xref:System.Threading.CountdownEvent> est conçu pour les scénarios dans lesquels vous utiliseriez plutôt un <xref:System.Threading.ManualResetEvent> ou <xref:System.Threading.ManualResetEventSlim> et décrémenteriez manuellement une variable avant de signaler l'événement.  Par exemple, vous pouvez juste créer un <xref:System.Threading.CountdownEvent> qui a un nombre de signal de 5 dans un scénario de bifurcation\/jointure, puis démarrer cinq éléments de travail sur le pool de threads et faire en sorte que chaque élément de travail appelle <xref:System.Threading.CountdownEvent.Signal%2A> lorsqu'il est terminé.  Chaque appel à <xref:System.Threading.CountdownEvent.Signal%2A> décrémente le nombre de signal par 1.  Sur le thread principal, l'appel à <xref:System.Threading.CountdownEvent.Wait%2A> se bloquera jusqu'à ce que le nombre de signal soit nul.  
  
> [!NOTE]
>  Pour le code qui n'a pas à interagir avec les API de synchronisation .NET Framework héritées, envisagez d'utiliser des objets <xref:System.Threading.Tasks.Task?displayProperty=fullName> ou la méthode <xref:System.Threading.Tasks.Parallel.Invoke%2A> pour une approche encore plus facile du parallélisme de bifurcation\-jointure.  
  
 <xref:System.Threading.CountdownEvent> comprend ces fonctionnalités supplémentaires :  
  
-   L'opération d'attente peut être annulée à l'aide des jetons d'annulation.  
  
-   Son nombre de signal peut être incrémenté après que l'instance a été créée.  
  
-   Les instances peuvent être réutilisées après que <xref:System.Threading.CountdownEvent.Wait%2A> a été retourné en appelant la méthode <xref:System.Threading.CountdownEvent.Reset%2A>.  
  
-   Les instances exposent un <xref:System.Threading.WaitHandle> pour l'intégration avec d'autres API de synchronisation .NET Framework telle que <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## Utilisation de base  
 L'exemple suivant montre comment utiliser un <xref:System.Threading.CountdownEvent> avec des éléments de travail <xref:System.Threading.ThreadPool>.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## CountdownEvent avec annulation  
 L'exemple suivant indique comment annuler l'opération d'attente sur <xref:System.Threading.CountdownEvent> à l'aide d'un jeton d'annulation.  Le modèle de base suit le modèle pour l'annulation unifiée, présentée dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].  Pour plus d'informations, consultez [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Notez que l'opération d'attente n'annule pas les threads qui le signalent.  En général, l'annulation est appliquée à une opération logique, et qui peut inclure l'attente sur l'événement ainsi que tous les éléments de travail que l'attente synchronise.  Dans cet exemple, une copie du même jeton d'annulation est passée à chaque élément de travail afin qu'il puisse répondre à la demande d'annulation.  
  
## Voir aussi  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)