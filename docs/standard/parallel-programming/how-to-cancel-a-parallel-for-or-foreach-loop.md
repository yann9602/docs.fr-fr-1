---
title: "How to: Cancel a Parallel.For or ForEach Loop | Microsoft Docs"
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
  - "parallel foreach loop, how to cancel"
  - "parallel for loops, how to cancel"
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# How to: Cancel a Parallel.For or ForEach Loop
Les méthodes <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> prennent en charge l'annulation via l'utilisation de jetons d'annulation.  Pour plus d'informations sur l'annulation en général, consultez [Annulation](../../../docs/standard/threading/cancellation-in-managed-threads.md) \(page éventuellement en anglais\).  Dans une boucle parallèle, vous fournissez <xref:System.Threading.CancellationToken> à la méthode dans le paramètre <xref:System.Threading.Tasks.ParallelOptions> puis joignez l'appel parallèle dans un bloc try\-catch.  
  
## Exemple  
 L'exemple suivant montre comment annuler un appel à <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName>.  Vous pouvez utiliser la même approche pour un appel <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName>.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Si le jeton qui signale l'annulation est le même jeton que celui spécifié dans l'instance <xref:System.Threading.Tasks.ParallelOptions>, la boucle parallèle lèvera une <xref:System.OperationCanceledException> unique sur l'annulation.  Si un autre jeton provoque l'annulation, la boucle lèvera une <xref:System.AggregateException> avec une <xref:System.OperationCanceledException> comme InnerException.  
  
## Voir aussi  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)