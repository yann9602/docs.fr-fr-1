---
title: "Comment : annuler une tâche et ses enfants"
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
helpviewer_keywords: tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 374068694a3aa9724905964717dc5e77c09fc0ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-task-and-its-children"></a>Comment : annuler une tâche et ses enfants
Les exemples suivants montrent comment effectuer les tâches suivantes :  
  
1.  Créer et lancer une tâche annulable.  
  
2.  Passer un jeton d’annulation à votre délégué utilisateur et éventuellement à l’instance de tâche.  
  
3.  Remarquer et répondre à la demande d’annulation dans votre délégué d’utilisateur.  
  
4.  Notez si vous le souhaitez sur le thread appelant que la tâche a été annulée.  
  
 Le thread appelant ne termine pas forcer la tâche ; Il signale seulement que l’annulation est demandée. Si la tâche est déjà en cours d’exécution, il est au délégué utilisateur de la demande et réagir de façon appropriée. Si l’annulation est demandée avant l’exécution de la tâche, puis le délégué d’utilisateur n’est jamais exécuté et l’objet de tâche passe à l’état Canceled.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment arrêter un <xref:System.Threading.Tasks.Task> et ses enfants en réponse à une demande d’annulation. Il montre également que lorsqu’un délégué utilisateur se termine en levant une <xref:System.Threading.Tasks.TaskCanceledException>, le thread appelant peut utiliser éventuellement le <xref:System.Threading.Tasks.Task.Wait%2A> méthode ou <xref:System.Threading.Tasks.Task.WaitAll%2A> méthode pour attendre les tâches se terminent. Dans ce cas, vous devez utiliser un `try/catch` bloc pour gérer les exceptions sur le thread appelant.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 Le <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classe est entièrement intégré au modèle d’annulation qui est basé sur le <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> et <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types. Pour plus d’informations, consultez [l’annulation dans les Threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md) et [l’annulation de tâche](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
 <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
 [Programmation asynchrone basée sur les tâches](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [Tâches enfants attachées et détachées](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
 [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
