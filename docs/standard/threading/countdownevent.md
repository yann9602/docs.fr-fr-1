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
# <a name="countdownevent"></a><span data-ttu-id="24918-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="24918-102">CountdownEvent</span></span>
<span data-ttu-id="24918-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>est une primitive de synchronisation qui débloque ses threads en attente après que qu’elle a été signalé un certain nombre de fois.</span><span class="sxs-lookup"><span data-stu-id="24918-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="24918-104"><xref:System.Threading.CountdownEvent>est conçu pour les scénarios dans lesquels vous utiliseriez à utiliser un <xref:System.Threading.ManualResetEvent> ou <xref:System.Threading.ManualResetEventSlim> et de décrémentation manuellement une variable avant de signaler l’événement.</span><span class="sxs-lookup"><span data-stu-id="24918-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="24918-105">Par exemple, dans un scénario de bifurcation/jointure, vous pouvez simplement créer un <xref:System.Threading.CountdownEvent> qui a un nombre de signal de 5, puis démarrer cinq éléments de travail sur le thread de pool et ont chaque élément de travail appelle <xref:System.Threading.CountdownEvent.Signal%2A> lorsqu’il est terminé.</span><span class="sxs-lookup"><span data-stu-id="24918-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="24918-106">Chaque appel à <xref:System.Threading.CountdownEvent.Signal%2A> décrémente le nombre de signal par 1.</span><span class="sxs-lookup"><span data-stu-id="24918-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="24918-107">Sur le thread principal, l’appel à <xref:System.Threading.CountdownEvent.Wait%2A> se bloque jusqu'à ce que le nombre de signal est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="24918-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24918-108">Pour le code qui n’a pas d’interagir avec les API de synchronisation .NET Framework héritées, envisagez d’utiliser <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objets ou <xref:System.Threading.Tasks.Parallel.Invoke%2A> méthode pour une approche plus facile pour exprimer le parallélisme de bifurcation-jointure.</span><span class="sxs-lookup"><span data-stu-id="24918-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="24918-109"><xref:System.Threading.CountdownEvent>présente les fonctionnalités supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="24918-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
-   <span data-ttu-id="24918-110">L’opération d’attente peut être annulée à l’aide des jetons d’annulation.</span><span class="sxs-lookup"><span data-stu-id="24918-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
-   <span data-ttu-id="24918-111">Son nombre de signal peut être incrémenté une fois que l’instance est créée.</span><span class="sxs-lookup"><span data-stu-id="24918-111">Its signal count can be incremented after the instance is created.</span></span>  
  
-   <span data-ttu-id="24918-112">Instances peuvent être réutilisées après <xref:System.Threading.CountdownEvent.Wait%2A> a retourné en appelant le <xref:System.Threading.CountdownEvent.Reset%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="24918-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
-   <span data-ttu-id="24918-113">Les instances exposent un <xref:System.Threading.WaitHandle> pour l’intégration avec d’autres API de synchronisation .NET Framework tels que <xref:System.Threading.WaitHandle.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="24918-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="24918-114">Utilisation de base</span><span class="sxs-lookup"><span data-stu-id="24918-114">Basic Usage</span></span>  
 <span data-ttu-id="24918-115">L’exemple suivant montre comment utiliser un <xref:System.Threading.CountdownEvent> avec <xref:System.Threading.ThreadPool> des éléments de travail.</span><span class="sxs-lookup"><span data-stu-id="24918-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="24918-116">CountdownEvent avec annulation</span><span class="sxs-lookup"><span data-stu-id="24918-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="24918-117">L’exemple suivant montre comment annuler l’opération d’attente sur <xref:System.Threading.CountdownEvent> à l’aide d’un jeton d’annulation.</span><span class="sxs-lookup"><span data-stu-id="24918-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="24918-118">Le modèle de base suit le modèle pour l’annulation unifiée, introduite dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24918-118">The basic pattern follows the model for unified cancellation, which is introduced in [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="24918-119">Pour plus d’informations, consultez [l’annulation dans les Threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="24918-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="24918-120">Notez que l’opération d’attente n’annule pas les threads qui le signalent.</span><span class="sxs-lookup"><span data-stu-id="24918-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="24918-121">En règle générale, l’annulation est appliquée à une opération logique, et qui peut inclure l’attente sur l’événement, ainsi que tous les éléments de travail que l’attente est en cours de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="24918-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="24918-122">Dans cet exemple, chaque élément de travail est passé à une copie de la même jeton d’annulation afin qu’il puisse répondre à la demande d’annulation.</span><span class="sxs-lookup"><span data-stu-id="24918-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24918-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24918-123">See Also</span></span>  
 [<span data-ttu-id="24918-124">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="24918-124">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
