---
title: "États des threads managés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 073fb19ef34ba32ccb5d5664413718a436563770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="managed-thread-states"></a><span data-ttu-id="5bf06-102">États des threads managés</span><span class="sxs-lookup"><span data-stu-id="5bf06-102">Managed Thread States</span></span>
<span data-ttu-id="5bf06-103">La propriété <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> fournit un masque de bits qui indique l’état du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="5bf06-103">The property <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> provides a bit mask that indicates the thread's current state.</span></span> <span data-ttu-id="5bf06-104">Un thread se trouve toujours dans au moins un des états possibles de l’énumération <xref:System.Threading.ThreadState> et peut être dans plusieurs états en même temps.</span><span class="sxs-lookup"><span data-stu-id="5bf06-104">A thread is always in at least one of the possible states in the <xref:System.Threading.ThreadState> enumeration, and can be in multiple states at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5bf06-105">L’état des threads n’est utile que dans quelques scénarios de débogage.</span><span class="sxs-lookup"><span data-stu-id="5bf06-105">Thread state is only of interest in a few debugging scenarios.</span></span> <span data-ttu-id="5bf06-106">Votre code ne doit jamais utiliser l’état des threads pour synchroniser les activités des threads.</span><span class="sxs-lookup"><span data-stu-id="5bf06-106">Your code should never use thread state to synchronize the activities of threads.</span></span>  
  
 <span data-ttu-id="5bf06-107">Quand vous créez un thread managé, il est dans l’état <xref:System.Threading.ThreadState.Unstarted> .</span><span class="sxs-lookup"><span data-stu-id="5bf06-107">When you create a managed thread, it is in the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="5bf06-108">Le thread reste dans l’état <xref:System.Threading.ThreadState.Unstarted> jusqu’à ce qu’il soit placé dans l’état Démarré par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="5bf06-108">The thread remains in the <xref:System.Threading.ThreadState.Unstarted> state until it is moved into the started state by the operating system.</span></span> <span data-ttu-id="5bf06-109">L’appel à <xref:System.Threading.Thread.Start%2A> informe le système d’exploitation que le thread peut être démarré ; il ne change pas l’état du thread.</span><span class="sxs-lookup"><span data-stu-id="5bf06-109">Calling <xref:System.Threading.Thread.Start%2A> lets the operating system know that the thread can be started; it does not change the state of the thread.</span></span>  
  
 <span data-ttu-id="5bf06-110">Les threads non managés qui entrent l’environnement managé sont déjà dans l’état Démarré.</span><span class="sxs-lookup"><span data-stu-id="5bf06-110">Unmanaged threads that enter the managed environment are already in the started state.</span></span> <span data-ttu-id="5bf06-111">Une fois qu’un thread est dans l’état Démarré, plusieurs actions peut le faire changer d’état.</span><span class="sxs-lookup"><span data-stu-id="5bf06-111">Once a thread is in the started state, a number of actions can cause it to change states.</span></span> <span data-ttu-id="5bf06-112">Le tableau suivant répertorie les actions qui provoquent un changement d’état, ainsi que le nouvel état correspondant.</span><span class="sxs-lookup"><span data-stu-id="5bf06-112">The following table lists the actions that cause a change of state, along with the corresponding new state.</span></span>  
  
|<span data-ttu-id="5bf06-113">Action</span><span class="sxs-lookup"><span data-stu-id="5bf06-113">Action</span></span>|<span data-ttu-id="5bf06-114">Nouvel état résultant</span><span class="sxs-lookup"><span data-stu-id="5bf06-114">Resulting new state</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="5bf06-115">Le constructeur de la classe <xref:System.Threading.Thread> est appelé.</span><span class="sxs-lookup"><span data-stu-id="5bf06-115">The constructor for the <xref:System.Threading.Thread> class is called.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="5bf06-116">Un autre thread appelle <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bf06-116">Another thread calls <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="5bf06-117">Le thread répond à <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> et démarre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5bf06-117">The thread responds to <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> and starts running.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="5bf06-118">Le thread appelle <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bf06-118">The thread calls <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="5bf06-119">Le thread appelle <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> sur un autre objet.</span><span class="sxs-lookup"><span data-stu-id="5bf06-119">The thread calls <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> on another object.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="5bf06-120">Le thread appelle <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> sur un autre thread.</span><span class="sxs-lookup"><span data-stu-id="5bf06-120">The thread calls <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> on another thread.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="5bf06-121">Un autre thread appelle <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bf06-121">Another thread calls <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.SuspendRequested>|  
|<span data-ttu-id="5bf06-122">Le thread répond à une <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> demande.</span><span class="sxs-lookup"><span data-stu-id="5bf06-122">The thread responds to a <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> request.</span></span>|<xref:System.Threading.ThreadState.Suspended>|  
|<span data-ttu-id="5bf06-123">Un autre thread appelle <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bf06-123">Another thread calls <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="5bf06-124">Un autre thread appelle <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bf06-124">Another thread calls <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.AbortRequested>|  
|<span data-ttu-id="5bf06-125">Le thread répond à une <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bf06-125">The thread responds to an <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<span data-ttu-id="5bf06-126"><xref:System.Threading.ThreadState.Aborted>, puis <xref:System.Threading.ThreadState.Stopped></span><span class="sxs-lookup"><span data-stu-id="5bf06-126"><xref:System.Threading.ThreadState.Aborted>, then <xref:System.Threading.ThreadState.Stopped></span></span>|  
  
 <span data-ttu-id="5bf06-127">Étant donné que l’état de <xref:System.Threading.ThreadState.Running> a la valeur 0, il n’est pas possible d’effectuer un test de bits pour découvrir cet état.</span><span class="sxs-lookup"><span data-stu-id="5bf06-127">Because the <xref:System.Threading.ThreadState.Running> state has a value of 0, it is not possible to perform a bit test to discover this state.</span></span> <span data-ttu-id="5bf06-128">Au lieu de cela, le test suivant (en pseudo-code) peut être utilisé :</span><span class="sxs-lookup"><span data-stu-id="5bf06-128">Instead, the following test (in pseudo-code) can be used:</span></span>  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 <span data-ttu-id="5bf06-129">Les threads se trouvent souvent dans plusieurs états à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="5bf06-129">Threads are often in more than one state at any given time.</span></span> <span data-ttu-id="5bf06-130">Par exemple, si un thread est bloqué sur un <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> appel et un autre thread appelle <xref:System.Threading.Thread.Abort%2A> sur ce même thread, le thread sera à la fois dans le <xref:System.Threading.ThreadState.WaitSleepJoin> et <xref:System.Threading.ThreadState.AbortRequested> États en même temps.</span><span class="sxs-lookup"><span data-stu-id="5bf06-130">For example, if a thread is blocked on a <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> call and another thread calls <xref:System.Threading.Thread.Abort%2A> on that same thread, the thread will be in both the <xref:System.Threading.ThreadState.WaitSleepJoin> and the <xref:System.Threading.ThreadState.AbortRequested> states at the same time.</span></span> <span data-ttu-id="5bf06-131">Dans ce cas, dès que le thread retourne de l’appel à <xref:System.Threading.Monitor.Wait%2A> ou est interrompu, il reçoit <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="5bf06-131">In that case, as soon as the thread returns from the call to <xref:System.Threading.Monitor.Wait%2A> or is interrupted, it will receive the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 <span data-ttu-id="5bf06-132">Une fois qu’un thread quitte l’état <xref:System.Threading.ThreadState.Unstarted> à la suite d’un appel à <xref:System.Threading.Thread.Start%2A>, il ne peut jamais revenir à l’état <xref:System.Threading.ThreadState.Unstarted> .</span><span class="sxs-lookup"><span data-stu-id="5bf06-132">Once a thread leaves the <xref:System.Threading.ThreadState.Unstarted> state as the result of a call to <xref:System.Threading.Thread.Start%2A>, it can never return to the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="5bf06-133">Un thread ne peut jamais quitter l’état <xref:System.Threading.ThreadState.Stopped> .</span><span class="sxs-lookup"><span data-stu-id="5bf06-133">A thread can never leave the <xref:System.Threading.ThreadState.Stopped> state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf06-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bf06-134">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [<span data-ttu-id="5bf06-135">Thread</span><span class="sxs-lookup"><span data-stu-id="5bf06-135">Threading</span></span>](../../../docs/standard/threading/index.md)
