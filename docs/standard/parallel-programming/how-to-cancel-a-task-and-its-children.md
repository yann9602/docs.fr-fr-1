---
title: "How to: Cancel a Task and Its Children | Microsoft Docs"
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
  - "tasks, how to cancel"
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# How to: Cancel a Task and Its Children
Ces exemples vous montrent comment effectuer les tâches suivantes :  
  
1.  Créer et lancer une tâche annulable ;  
  
2.  Passer un jeton d'annulation à votre délégué utilisateur et éventuellement à l'instance de tâche ;  
  
3.  Remarquer et répondre à la requête d'annulation dans votre délégué utilisateur ;  
  
4.  Éventuellement remarquer sur le thread appelant que la tâche a été annulée.  
  
 Le thread appelant ne termine pas la tâche de force ; il signale seulement que l'annulation est demandée.  Si la tâche s'exécute déjà, c'est au délégué utilisateur de remarquer la requête et d'y répondre en conséquence.  Si l'annulation est demandée avant l'exécution de la tâche, le délégué utilisateur n'est pas exécuté et l'objet tâche effectue une transition à l'état d'annulation.  
  
## Exemple  
 Cet exemple indique comment terminer un <xref:System.Threading.Tasks.Task> et ses enfants en réponse à une requête d'annulation.  Il montre également que lorsqu'un délégué utilisateur se termine en levant une <xref:System.Threading.Tasks.TaskCanceledException>, le thread appelant peut utiliser éventuellement la méthode <xref:System.Threading.Tasks.Task.Wait%2A> ou <xref:System.Threading.Tasks.Task.WaitAll%2A> pour attendre que les tâches se terminent.  Dans ce cas, le délégué doit utiliser un bloc `try/catch` pour gérer les exceptions sur le thread appelant.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 La classe <xref:System.Threading.Tasks.Task?displayProperty=fullName> est pleinement intégrée au modèle d'annulation basé sur les types <xref:System.Threading.CancellationTokenSource?displayProperty=fullName> et <xref:System.Threading.CancellationToken?displayProperty=fullName>.  Pour plus d’informations, consultez [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md) et [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
## Voir aussi  
 <xref:System.Threading.CancellationTokenSource?displayProperty=fullName>   
 <xref:System.Threading.CancellationToken?displayProperty=fullName>   
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.Task%601?displayProperty=fullName>   
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)   
 [Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)