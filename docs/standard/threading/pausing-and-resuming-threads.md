---
title: Suspension et reprise des threads
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
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a><span data-ttu-id="328e8-102">Suspension et reprise des threads</span><span class="sxs-lookup"><span data-stu-id="328e8-102">Pausing and Resuming Threads</span></span>
<span data-ttu-id="328e8-103">Les méthodes les plus courantes permettant de synchroniser les activités de threads consistent à bloquer et à diffuser des threads, ou à verrouiller des objets ou des régions du code.</span><span class="sxs-lookup"><span data-stu-id="328e8-103">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="328e8-104">Pour plus d’informations sur ces mécanismes de verrouillage et de blocage, voir [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="328e8-104">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="328e8-105">Vous pouvez également avoir des threads en veille.</span><span class="sxs-lookup"><span data-stu-id="328e8-105">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="328e8-106">Quand des threads sont bloqués ou en veille, vous pouvez utiliser une <xref:System.Threading.ThreadInterruptedException> pour les débloquer ou les réveiller.</span><span class="sxs-lookup"><span data-stu-id="328e8-106">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="328e8-107">La méthode Thread.Sleep</span><span class="sxs-lookup"><span data-stu-id="328e8-107">The Thread.Sleep Method</span></span>  
 <span data-ttu-id="328e8-108">Appel de la <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> méthode oblige le thread actuel bloquer immédiatement pour le nombre de millisecondes ou de l’intervalle de temps que vous passez à la méthode et obtient le reste de sa tranche de temps à un autre thread.</span><span class="sxs-lookup"><span data-stu-id="328e8-108">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="328e8-109">Une fois l’intervalle expiré, l’exécution du thread en veille reprend.</span><span class="sxs-lookup"><span data-stu-id="328e8-109">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="328e8-110">Un thread ne peut pas appeler <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> sur un autre thread.</span><span class="sxs-lookup"><span data-stu-id="328e8-110">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="328e8-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>est une méthode statique qui entraîne systématiquement la mise en veille du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="328e8-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="328e8-112">Appel de <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> avec la valeur <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> entraîne un thread en veille jusqu'à ce qu’il soit interrompu par un autre thread qui appelle la <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> méthode sur le thread en veille, ou jusqu'à ce qu’il se termine par un appel à son <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="328e8-112">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="328e8-113">L’exemple suivant illustre les deux méthodes d’interruption d’un thread en veille.</span><span class="sxs-lookup"><span data-stu-id="328e8-113">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="328e8-114">Interruption de threads</span><span class="sxs-lookup"><span data-stu-id="328e8-114">Interrupting Threads</span></span>  
 <span data-ttu-id="328e8-115">Vous pouvez interrompre un thread en attente en appelant le <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> méthode sur le thread bloqué pour lever une <xref:System.Threading.ThreadInterruptedException>, qui arrête le thread de l’appel bloquant.</span><span class="sxs-lookup"><span data-stu-id="328e8-115">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="328e8-116">Le thread doit intercepter la <xref:System.Threading.ThreadInterruptedException> et faire tout le nécessaire pour continuer à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="328e8-116">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="328e8-117">Si le thread ignore l'exception, le runtime intercepte l'exception et arrête le thread.</span><span class="sxs-lookup"><span data-stu-id="328e8-117">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="328e8-118">Si le thread cible n'est pas bloqué quand <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> est appelé, le thread ne sera pas interrompu avant d'être bloqué.</span><span class="sxs-lookup"><span data-stu-id="328e8-118">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="328e8-119">Si le thread n'est jamais bloqué, il peut se terminer sans jamais être interrompu.</span><span class="sxs-lookup"><span data-stu-id="328e8-119">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="328e8-120">En cas d'attente managée, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> réveillent le thread immédiatement.</span><span class="sxs-lookup"><span data-stu-id="328e8-120">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="328e8-121">Cas d’une attente non managée (par exemple, une appel de plateforme pour Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) fonction), ni <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ni <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> peut prendre le contrôle du thread jusqu'à ce qu’il retourne vers ou appelle dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="328e8-121">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="328e8-122">Dans du code managé, le comportement est le suivant :</span><span class="sxs-lookup"><span data-stu-id="328e8-122">In managed code, the behavior is as follows:</span></span>  
  
-   <span data-ttu-id="328e8-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> réveille un thread en attente et provoque la levée d'une <xref:System.Threading.ThreadInterruptedException> dans le thread de destination.</span><span class="sxs-lookup"><span data-stu-id="328e8-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
-   <span data-ttu-id="328e8-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>réveille un thread de l’attente, il est peut-être en et entraîne un <xref:System.Threading.ThreadAbortException> levée sur le thread.</span><span class="sxs-lookup"><span data-stu-id="328e8-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="328e8-125">Pour plus d’informations, voir [Destruction de threads](../../../docs/standard/threading/destroying-threads.md).</span><span class="sxs-lookup"><span data-stu-id="328e8-125">For details, see [Destroying Threads](../../../docs/standard/threading/destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328e8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="328e8-126">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [<span data-ttu-id="328e8-127">Thread</span><span class="sxs-lookup"><span data-stu-id="328e8-127">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="328e8-128">Utilisation des threads et du threading</span><span class="sxs-lookup"><span data-stu-id="328e8-128">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="328e8-129">Vue d’ensemble des primitives de synchronisation</span><span class="sxs-lookup"><span data-stu-id="328e8-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
