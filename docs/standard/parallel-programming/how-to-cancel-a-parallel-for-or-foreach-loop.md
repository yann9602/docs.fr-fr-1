---
title: "Comment : annuler une boucle Parallel.For ou ForEach"
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
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Comment : annuler une boucle Parallel.For ou ForEach
Le <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> méthodes prennent en charge l’annulation via l’utilisation de jetons d’annulation. Pour plus d’informations sur l’annulation en général, consultez [annulation](../../../docs/standard/threading/cancellation-in-managed-threads.md). Dans une boucle parallèle, vous fournissez le <xref:System.Threading.CancellationToken> à la méthode dans le <xref:System.Threading.Tasks.ParallelOptions> paramètre et puis joignez l’appel parallèle dans un bloc try-catch.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment annuler un appel à <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Vous pouvez appliquer la même approche pour un <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> appeler.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Si le jeton qui signale l’annulation est le même jeton qui est spécifié dans le <xref:System.Threading.Tasks.ParallelOptions> de l’instance, puis la boucle parallèle lèvera une seule <xref:System.OperationCanceledException> d’annulation. Si un autre jeton provoque l’annulation, la boucle lèvera une <xref:System.AggregateException> avec un <xref:System.OperationCanceledException> comme InnerException.  
  
## <a name="see-also"></a>Voir aussi  
 [Parallélisme de données](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
