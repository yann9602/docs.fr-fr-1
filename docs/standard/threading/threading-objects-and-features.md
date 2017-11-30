---
title: "Fonctionnalités et objets de threading"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a73e5c60a661c171e9e46e6307484cf5e0e6b80
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="92c54-102">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="92c54-102">Threading Objects and Features</span></span>
<span data-ttu-id="92c54-103">.NET Framework fournit plusieurs objets permettant de créer et de gérer des applications multithread.</span><span class="sxs-lookup"><span data-stu-id="92c54-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="92c54-104">Les threads managés sont représentés par la classe <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="92c54-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="92c54-105">La classe <xref:System.Threading.ThreadPool> permet de créer et de gérer facilement des tâches d'arrière-plan multithread.</span><span class="sxs-lookup"><span data-stu-id="92c54-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="92c54-106">La classe <xref:System.ComponentModel.BackgroundWorker> permet la même chose pour les tâches qui interagissent avec l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="92c54-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="92c54-107">La classe <xref:System.Threading.Timer> exécute des tâches en arrière-plan à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="92c54-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="92c54-108">De plus, plusieurs classes permettent de synchroniser des activités de threads, y compris les classes <xref:System.Threading.Semaphore> et <xref:System.Threading.EventWaitHandle> de .NET Framework version 2.0 et ultérieures.</span><span class="sxs-lookup"><span data-stu-id="92c54-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="92c54-109">Les fonctionnalités de ces classes sont comparées dans la section [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="92c54-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92c54-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="92c54-110">In This Section</span></span>  
 [<span data-ttu-id="92c54-111">Pool de threads managés</span><span class="sxs-lookup"><span data-stu-id="92c54-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="92c54-112">Décrit la classe **ThreadPool**, qui vous permet de demander à un thread d’exécuter une tâche sans avoir à gérer les threads vous-même.</span><span class="sxs-lookup"><span data-stu-id="92c54-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="92c54-113">Minuteries</span><span class="sxs-lookup"><span data-stu-id="92c54-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="92c54-114">Explique comment utiliser une **minuterie** pour spécifier le délégué devant être appelé à une heure spécifique.</span><span class="sxs-lookup"><span data-stu-id="92c54-114">Explains how to use a **Timer** to specify a delegate to be called at a specified time.</span></span>  
  
 [<span data-ttu-id="92c54-115">Moniteurs</span><span class="sxs-lookup"><span data-stu-id="92c54-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="92c54-116">Explique comment utiliser la classe **Monitor** pour synchroniser l’accès à un membre ou pour créer vos propres types de gestion de threads.</span><span class="sxs-lookup"><span data-stu-id="92c54-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="92c54-117">Descripteurs d’attente</span><span class="sxs-lookup"><span data-stu-id="92c54-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="92c54-118">Décrit la classe <xref:System.Threading.WaitHandle>, qui est la classe de base abstraite pour les handles d'attente d'événements, les mutex et les sémaphores et qui permet d'attendre plusieurs événements de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="92c54-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="92c54-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="92c54-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="92c54-120">Décrit les handles d’attente d’événements managés qui sont utilisés pour synchroniser les activités de thread en signalant et en attendant des signaux.</span><span class="sxs-lookup"><span data-stu-id="92c54-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="92c54-121">Mutex</span><span class="sxs-lookup"><span data-stu-id="92c54-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="92c54-122">Explique comment utiliser un <xref:System.Threading.Mutex> pour synchroniser l’accès à un objet ou pour créer vos propres mécanismes de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="92c54-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="92c54-123">Opérations verrouillées</span><span class="sxs-lookup"><span data-stu-id="92c54-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="92c54-124">Explique comment utiliser la classe <xref:System.Threading.Interlocked> pour incrémenter ou décrémenter une valeur et la stocker dans une même opération atomique.</span><span class="sxs-lookup"><span data-stu-id="92c54-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="92c54-125">Verrous de lecteur-writer</span><span class="sxs-lookup"><span data-stu-id="92c54-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="92c54-126">Définit un verrou qui implémente une sémantique à enregistreur unique/lecteurs multiples.</span><span class="sxs-lookup"><span data-stu-id="92c54-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="92c54-127">Semaphore et SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="92c54-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="92c54-128">Décrit les objets <xref:System.Threading.Semaphore> et explique comment les utiliser pour contrôler l'accès aux ressources limitées.</span><span class="sxs-lookup"><span data-stu-id="92c54-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="92c54-129">Vue d’ensemble des primitives de synchronisation</span><span class="sxs-lookup"><span data-stu-id="92c54-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="92c54-130">Compare les fonctionnalités des classes .NET Framework fournies pour verrouiller et synchroniser les threads managés.</span><span class="sxs-lookup"><span data-stu-id="92c54-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="92c54-131">Barrier</span><span class="sxs-lookup"><span data-stu-id="92c54-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="92c54-132">Décrit les objets <xref:System.Threading.Barrier> qui implémentent le modèle de cloisonnement pour la coordination des threads dans les opérations planifiées.</span><span class="sxs-lookup"><span data-stu-id="92c54-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="92c54-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="92c54-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="92c54-134">Décrit <xref:System.Threading.SpinLock>, une alternative légère à la classe Monitor pour certains scénarios de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="92c54-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="92c54-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="92c54-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="92c54-136">Décrit <xref:System.Threading.SpinWait>, une primitive de synchronisation de bas niveau qui exécute une attente active avant d'initialiser une attente basée sur le noyau.</span><span class="sxs-lookup"><span data-stu-id="92c54-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="92c54-137">Référence</span><span class="sxs-lookup"><span data-stu-id="92c54-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="92c54-138">Fournit la documentation de référence pour la classe **Thread** qui représente un thread managé, qu’elle provienne de code non managé ou qu’elle ait été créée dans une application managée.</span><span class="sxs-lookup"><span data-stu-id="92c54-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="92c54-139">Permet aux tâches d’arrière-plan d’interagir avec l’interface utilisateur, en communiquant via des événements déclenchés sur le thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="92c54-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="92c54-140">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="92c54-140">Related Sections</span></span>  
 [<span data-ttu-id="92c54-141">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="92c54-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="92c54-142">Explique comment les ports de terminaison asynchrones d'E/S utilisent le pool de threads pour exiger un traitement uniquement quand une opération d'entrée/sortie est terminée.</span><span class="sxs-lookup"><span data-stu-id="92c54-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="92c54-143">La bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="92c54-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="92c54-144">Décrit l'approche recommandée pour la programmation multithread dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="92c54-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
