---
title: "Meilleures pratiques pour le threading managé"
ms.custom: 
ms.date: 11/30/2017
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
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e396bb1f6a710e49e311ca1526a7aae9bca7bf90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="0900f-102">Meilleures pratiques pour le threading managé</span><span class="sxs-lookup"><span data-stu-id="0900f-102">Managed Threading Best Practices</span></span>
<span data-ttu-id="0900f-103">Le multithreading nécessite une programmation attentive.</span><span class="sxs-lookup"><span data-stu-id="0900f-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="0900f-104">Pour réduire la complexité de la plupart des tâches, il vous suffit de mettre en file d’attente les requêtes à exécuter par les threads d’un pool de threads.</span><span class="sxs-lookup"><span data-stu-id="0900f-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="0900f-105">Cet article vous permet de remédier aux situations plus complexes, telles que la coordination du travail de plusieurs threads ou la gestion des threads bloqués.</span><span class="sxs-lookup"><span data-stu-id="0900f-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0900f-106">À compter de .NET Framework 4, la bibliothèque parallèle de tâches et PLINQ fournissent des API qui réduire la complexité et les risques de la programmation multithread.</span><span class="sxs-lookup"><span data-stu-id="0900f-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="0900f-107">Pour plus d’informations, consultez [programmation parallèle dans .NET](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="0900f-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="0900f-108">Interblocages et conditions de concurrence</span><span class="sxs-lookup"><span data-stu-id="0900f-108">Deadlocks and Race Conditions</span></span>  
 <span data-ttu-id="0900f-109">Le multithreading résout les problèmes de débit et de réactivité, mais, ce faisant, occasionne de nouveaux problèmes : les interblocages et les conditions de concurrence.</span><span class="sxs-lookup"><span data-stu-id="0900f-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="0900f-110">Interblocages (deadlocks)</span><span class="sxs-lookup"><span data-stu-id="0900f-110">Deadlocks</span></span>  
 <span data-ttu-id="0900f-111">Un interblocage se produit lorsque chacun des deux threads tente de verrouiller une ressource déjà verrouillée par l’autre thread.</span><span class="sxs-lookup"><span data-stu-id="0900f-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="0900f-112">Aucun des deux threads ne peut donc poursuivre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0900f-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="0900f-113">De nombreuses méthodes des classes de threading managé fournissent des délais d’expiration conçus pour faciliter la détection des interblocages.</span><span class="sxs-lookup"><span data-stu-id="0900f-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="0900f-114">Par exemple, le code suivant tente d’acquérir un verrou sur un objet nommé `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="0900f-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="0900f-115">Si le verrou n’est pas obtenu en 300 millisecondes, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="0900f-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="0900f-116">Conditions de concurrence</span><span class="sxs-lookup"><span data-stu-id="0900f-116">Race Conditions</span></span>  
 <span data-ttu-id="0900f-117">Une condition de concurrence est un bogue qui survient lorsque le résultat d’un programme dépend du thread qui atteint le premier un bloc de code spécifique.</span><span class="sxs-lookup"><span data-stu-id="0900f-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="0900f-118">L’exécution du programme à plusieurs reprises produit des résultats différents, et le résultat d’une exécution donnée n’est donc pas prévisible.</span><span class="sxs-lookup"><span data-stu-id="0900f-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="0900f-119">Un exemple simple de condition de concurrence correspond à l’incrémentation d’un champ.</span><span class="sxs-lookup"><span data-stu-id="0900f-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="0900f-120">Supposons qu’une classe comporte un champ **static** privé (**Shared** en Visual Basic) qui est incrémenté chaque fois qu’une instance de la classe est créée, à l’aide d’un code tel que `objCt++;` (C#) ou `objCt += 1` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0900f-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="0900f-121">Cette opération nécessite le chargement de la valeur de `objCt` dans un registre, l’incrémentation de la valeur, puis son stockage dans `objCt`.</span><span class="sxs-lookup"><span data-stu-id="0900f-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="0900f-122">Dans une application multithread, il est possible qu’un thread ayant chargé et incrémenté la valeur soit devancé par un autre thread qui exécute ces trois étapes ; lorsque le premier thread reprend l’exécution et stocke sa valeur, il remplace alors la valeur de `objCt` sans tenir compte du fait qu’elle a changé dans l’intervalle.</span><span class="sxs-lookup"><span data-stu-id="0900f-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="0900f-123">Cette condition de concurrence critique est facile à éviter en utilisant des méthodes de la <xref:System.Threading.Interlocked> class, telle que <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0900f-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0900f-124">Pour découvrir d’autres techniques de synchronisation des données entre plusieurs threads, consultez l’article [Synchronisation des données pour le multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="0900f-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="0900f-125">Des conditions de concurrence peuvent également survenir lorsque vous synchronisez les activités de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="0900f-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="0900f-126">Chaque fois que vous écrivez une ligne de code, vous devez prendre en compte ce qui peut se produire si un thread est devancé par un autre thread avant d’avoir exécuté la ligne (ou avant toute instruction machine individuelle composant la ligne).</span><span class="sxs-lookup"><span data-stu-id="0900f-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="number-of-processors"></a><span data-ttu-id="0900f-127">Nombre de processeurs</span><span class="sxs-lookup"><span data-stu-id="0900f-127">Number of Processors</span></span>  
 <span data-ttu-id="0900f-128">La plupart des ordinateurs sont désormais équipés de plusieurs processeurs (également appelés cœurs), y compris les petits appareils, tels que les tablettes et les téléphones.</span><span class="sxs-lookup"><span data-stu-id="0900f-128">Most computers now have multiple processors (also called cores), even small devices such as tablets and phones.</span></span> <span data-ttu-id="0900f-129">Si vous développez des logiciels également destinés à s’exécuter sur des ordinateurs monoprocesseur, vous devez savoir que le multithreading résout différents problèmes pour les ordinateurs monoprocesseur et multiprocesseur.</span><span class="sxs-lookup"><span data-stu-id="0900f-129">If you know you're developing software that will also run on single-processor computers, you should be aware that multithreading solves different problems for single-processor computers and multiprocessor computers.</span></span>  
  
### <a name="multiprocessor-computers"></a><span data-ttu-id="0900f-130">Ordinateurs multiprocesseur</span><span class="sxs-lookup"><span data-stu-id="0900f-130">Multiprocessor Computers</span></span>  
 <span data-ttu-id="0900f-131">Le multithreading offre un débit plus élevé.</span><span class="sxs-lookup"><span data-stu-id="0900f-131">Multithreading provides greater throughput.</span></span> <span data-ttu-id="0900f-132">Dix processeurs peuvent effectuer dix fois le travail d’un seul processeur, mais uniquement si ce travail est divisé afin que les dix processeurs puissent le traiter simultanément. Les threads offrent un moyen simple de diviser le travail et d’exploiter la puissance de traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="0900f-132">Ten processors can do ten times the work of one, but only if the work is divided so that all ten can be working at once; threads provide an easy way to divide the work and exploit the extra processing power.</span></span> <span data-ttu-id="0900f-133">Si vous utilisez le multithreading sur un ordinateur multiprocesseur :</span><span class="sxs-lookup"><span data-stu-id="0900f-133">If you use multithreading on a multiprocessor computer:</span></span>  
  
-   <span data-ttu-id="0900f-134">Le nombre de threads pouvant s’exécuter simultanément est limité par le nombre de processeurs.</span><span class="sxs-lookup"><span data-stu-id="0900f-134">The number of threads that can execute concurrently is limited by the number of processors.</span></span>  
  
-   <span data-ttu-id="0900f-135">Un thread d’arrière-plan s’exécute uniquement lorsque le nombre de threads de premier plan qui s’exécutent est inférieur au nombre de processeurs.</span><span class="sxs-lookup"><span data-stu-id="0900f-135">A background thread executes only when the number of foreground threads executing is smaller than the number of processors.</span></span>  
  
-   <span data-ttu-id="0900f-136">Lorsque vous appelez le <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> méthode sur un thread, ce thread peut ou peut ne pas démarrer l’exécuter immédiatement, selon le nombre de processeurs et le nombre de threads actuellement en attente d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0900f-136">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread might or might not start executing immediately, depending on the number of processors and the number of threads currently waiting to execute.</span></span>  
  
-   <span data-ttu-id="0900f-137">Des conditions de concurrence peuvent survenir, non seulement lorsque des threads sont devancés de manière inattendue, mais également parce que deux threads qui s’exécutent sur différents processeurs risquent d’entrer en concurrence pour atteindre le même bloc de code.</span><span class="sxs-lookup"><span data-stu-id="0900f-137">Race conditions can occur not only because threads are preempted unexpectedly, but because two threads executing on different processors might be racing to reach the same code block.</span></span>  
  
### <a name="single-processor-computers"></a><span data-ttu-id="0900f-138">Ordinateurs monoprocesseur</span><span class="sxs-lookup"><span data-stu-id="0900f-138">Single-Processor Computers</span></span>  
 <span data-ttu-id="0900f-139">Le multithreading offre une meilleure réactivité à l’utilisateur de l’ordinateur et utilise la durée d’inactivité pour les tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="0900f-139">Multithreading provides greater responsiveness to the computer user, and uses idle time for background tasks.</span></span> <span data-ttu-id="0900f-140">Si vous utilisez le multithreading sur un ordinateur monoprocesseur :</span><span class="sxs-lookup"><span data-stu-id="0900f-140">If you use multithreading on a single-processor computer:</span></span>  
  
-   <span data-ttu-id="0900f-141">Un seul thread s’exécute à tout moment.</span><span class="sxs-lookup"><span data-stu-id="0900f-141">Only one thread runs at any instant.</span></span>  
  
-   <span data-ttu-id="0900f-142">Un thread d’arrière-plan s’exécute uniquement lorsque le thread utilisateur principal est inactif.</span><span class="sxs-lookup"><span data-stu-id="0900f-142">A background thread executes only when the main user thread is idle.</span></span> <span data-ttu-id="0900f-143">Un thread de premier plan qui s’exécute constamment prive les threads d’arrière-plan de temps processeur.</span><span class="sxs-lookup"><span data-stu-id="0900f-143">A foreground thread that executes constantly starves background threads of processor time.</span></span>  
  
-   <span data-ttu-id="0900f-144">Lorsque vous appelez le <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> méthode sur un thread, ce thread ne pas s’exécute jusqu'à ce que le thread en cours génère ou est devancé par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="0900f-144">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread does not start executing until the current thread yields or is preempted by the operating system.</span></span>  
  
-   <span data-ttu-id="0900f-145">Les conditions de concurrence surviennent généralement parce que le programmeur n’a pas anticipé le fait qu’un thread puisse être devancé à un moment inopportun, ce qui permet parfois à un autre thread d’atteindre un bloc de code le premier.</span><span class="sxs-lookup"><span data-stu-id="0900f-145">Race conditions typically occur because the programmer did not anticipate the fact that a thread can be preempted at an awkward moment, sometimes allowing another thread to reach a code block first.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="0900f-146">Membres static et constructeurs static</span><span class="sxs-lookup"><span data-stu-id="0900f-146">Static Members and Static Constructors</span></span>  
 <span data-ttu-id="0900f-147">Une classe n’est pas initialisée tant que son constructeur de classe (constructeur `static` en C#, `Shared Sub New` en Visual Basic) n’a pas fini de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="0900f-147">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="0900f-148">Pour empêcher l’exécution de code sur un type qui n’est pas initialisé, le common language runtime bloque tous les appels d’autres threads aux membres `static` de la classe (membres `Shared` en Visual Basic) jusqu’à la fin de l’exécution du constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="0900f-148">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="0900f-149">Par exemple, si un constructeur de classe démarre un nouveau thread, et que la procédure de thread appelle un membre `static` de la classe, le nouveau thread se bloque jusqu’à la fin du constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="0900f-149">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="0900f-150">Cela s’applique à n’importe quel type pouvant comporter un constructeur `static`.</span><span class="sxs-lookup"><span data-stu-id="0900f-150">This applies to any type that can have a `static` constructor.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="0900f-151">Recommandations générales</span><span class="sxs-lookup"><span data-stu-id="0900f-151">General Recommendations</span></span>  
 <span data-ttu-id="0900f-152">Lorsque vous utilisez plusieurs threads, tenez compte des recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0900f-152">Consider the following guidelines when using multiple threads:</span></span>  
  
-   <span data-ttu-id="0900f-153">N’utilisez pas <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour mettre fin à d’autres threads.</span><span class="sxs-lookup"><span data-stu-id="0900f-153">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="0900f-154">L’appel de la méthode **Abort** sur un autre thread équivaut à lever une exception sur ce dernier sans connaître le stade précis du traitement atteint par ce thread.</span><span class="sxs-lookup"><span data-stu-id="0900f-154">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
-   <span data-ttu-id="0900f-155">N’utilisez pas <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> pour synchroniser les activités de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="0900f-155">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="0900f-156">Utilisez <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, et <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="0900f-156">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
-   <span data-ttu-id="0900f-157">Ne contrôlez pas l’exécution des threads de travail à partir de votre programme principal (à l’aide d’événements, par exemple).</span><span class="sxs-lookup"><span data-stu-id="0900f-157">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="0900f-158">Concevez plutôt votre programme pour que les threads de travail soient chargés d’attendre que le travail devienne disponible, d’exécuter ce travail, puis d’en informer les autres parties de votre programme lorsqu’ils ont terminé.</span><span class="sxs-lookup"><span data-stu-id="0900f-158">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="0900f-159">Si vos threads de travail ne se bloquent pas, envisagez d’utiliser les threads d’un pool de threads.</span><span class="sxs-lookup"><span data-stu-id="0900f-159">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="0900f-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>est utile dans les situations où les threads de travail se bloquent.</span><span class="sxs-lookup"><span data-stu-id="0900f-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
-   <span data-ttu-id="0900f-161">N’utilisez pas de types en tant qu’objets de verrou.</span><span class="sxs-lookup"><span data-stu-id="0900f-161">Don't use types as lock objects.</span></span> <span data-ttu-id="0900f-162">Autrement dit, évitez comme code `lock(typeof(X))` en c# ou `SyncLock(GetType(X))` en Visual Basic, ou l’utilisation de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> avec <xref:System.Type> objets.</span><span class="sxs-lookup"><span data-stu-id="0900f-162">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="0900f-163">Pour un type donné, il existe une seule instance de <xref:System.Type?displayProperty=nameWithType> par domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="0900f-163">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="0900f-164">Si le type sur lequel vous utilisez un verrou est public, un code différent du vôtre peut utiliser des verrous sur ce type, entraînant ainsi des interblocages.</span><span class="sxs-lookup"><span data-stu-id="0900f-164">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="0900f-165">Pour découvrir les autres problèmes, consultez l’article [Meilleures pratiques pour la fiabilité](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="0900f-165">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
-   <span data-ttu-id="0900f-166">Procédez avec précaution lorsque vous utilisez des verrous sur des instances, par exemple `lock(this)` en C# ou `SyncLock(Me)` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0900f-166">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="0900f-167">Si un autre code de votre application, externe au type, utilise un verrou sur l’objet, des interblocages risquent de se produire.</span><span class="sxs-lookup"><span data-stu-id="0900f-167">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
-   <span data-ttu-id="0900f-168">Assurez-vous qu’un thread entré dans un moniteur quitte toujours ce dernier, même si une exception se produit pendant que le thread se trouve dans le moniteur.</span><span class="sxs-lookup"><span data-stu-id="0900f-168">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="0900f-169">C# [verrou](~/docs/csharp/language-reference/keywords/lock-statement.md) instruction et Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instruction fournissent ce comportement d’automatiquement, en utilisant un **enfin** bloc pour garantir que <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> est appelé.</span><span class="sxs-lookup"><span data-stu-id="0900f-169">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="0900f-170">Si vous n’êtes pas en mesure de garantir l’appel de la méthode **Exit**, vous pouvez modifier votre conception de façon à utiliser **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="0900f-170">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="0900f-171">Un mutex est automatiquement libéré lorsque le thread auquel il appartient a terminé.</span><span class="sxs-lookup"><span data-stu-id="0900f-171">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
-   <span data-ttu-id="0900f-172">Utilisez plusieurs threads pour les tâches qui nécessitent des ressources différentes, et évitez d’attribuer plusieurs threads à une même ressource.</span><span class="sxs-lookup"><span data-stu-id="0900f-172">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="0900f-173">Par exemple, vous tirerez avantage du fait que les tâches impliquant des E/S disposent de leur propre thread, car ce thread se bloquera lors des opérations d’E/S et permettra ainsi à d’autres threads de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="0900f-173">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="0900f-174">L’entrée utilisateur est une autre ressource tirant profit d’un thread dédié.</span><span class="sxs-lookup"><span data-stu-id="0900f-174">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="0900f-175">Sur un ordinateur monoprocesseur, une tâche qui exige de multiples calculs coexiste avec l’entrée utilisateur et avec les tâches qui impliquent des E/S, mais plusieurs tâches nécessitant de nombreux calculs entrent en concurrence les unes avec les autres.</span><span class="sxs-lookup"><span data-stu-id="0900f-175">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
-   <span data-ttu-id="0900f-176">Envisagez d’utiliser les méthodes de la <xref:System.Threading.Interlocked> classe pour les modifications d’état simple, au lieu d’utiliser le `lock` instruction (`SyncLock` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0900f-176">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="0900f-177">Le `lock` instruction est un bon outil à usage général, mais la <xref:System.Threading.Interlocked> classe fournit de meilleures performances pour les mises à jour qui doivent être atomiques.</span><span class="sxs-lookup"><span data-stu-id="0900f-177">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="0900f-178">En interne, elle exécute un seul préfixe de verrou s’il n’existe aucun conflit.</span><span class="sxs-lookup"><span data-stu-id="0900f-178">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="0900f-179">Lors des phases de révision du code, examinez le code semblable à celui des exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0900f-179">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="0900f-180">Dans le premier exemple, une variable d’état est incrémentée :</span><span class="sxs-lookup"><span data-stu-id="0900f-180">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="0900f-181">Vous pouvez améliorer les performances à l’aide de la <xref:System.Threading.Interlocked.Increment%2A> méthode à la place de la `lock` instruction, comme suit :</span><span class="sxs-lookup"><span data-stu-id="0900f-181">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0900f-182">Dans le .NET Framework version 2.0, le <xref:System.Threading.Interlocked.Add%2A> méthode fournit des mises à jour atomiques dans les incréments supérieurs à 1.</span><span class="sxs-lookup"><span data-stu-id="0900f-182">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method provides atomic updates in increments larger than 1.</span></span>  
  
     <span data-ttu-id="0900f-183">Dans le second exemple, une variable de type référence est uniquement mise à jour s’il s’agit d’une référence null (`Nothing` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0900f-183">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="0900f-184">Performances peuvent être améliorées en utilisant la <xref:System.Threading.Interlocked.CompareExchange%2A> méthode à la place, comme suit :</span><span class="sxs-lookup"><span data-stu-id="0900f-184">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0900f-185">Dans le .NET Framework version 2.0, le <xref:System.Threading.Interlocked.CompareExchange%2A> méthode a une surcharge générique qui peut être utilisée pour le remplacement de type sécurisé de tout type référence.</span><span class="sxs-lookup"><span data-stu-id="0900f-185">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.CompareExchange%2A> method has a generic overload that can be used for type-safe replacement of any reference type.</span></span>  
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="0900f-186">Recommandations relatives aux bibliothèques de classes</span><span class="sxs-lookup"><span data-stu-id="0900f-186">Recommendations for Class Libraries</span></span>  
 <span data-ttu-id="0900f-187">Lorsque vous concevez des bibliothèques de classes pour le multithreading, tenez compte des recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0900f-187">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
-   <span data-ttu-id="0900f-188">Dans la mesure du possible, évitez toute nécessité de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="0900f-188">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="0900f-189">Cette consigne s’applique tout particulièrement pour le code très sollicité.</span><span class="sxs-lookup"><span data-stu-id="0900f-189">This is especially true for heavily used code.</span></span> <span data-ttu-id="0900f-190">Par exemple, un algorithme peut être ajusté de façon à tolérer une condition de concurrence plutôt que de l’éliminer.</span><span class="sxs-lookup"><span data-stu-id="0900f-190">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="0900f-191">Une synchronisation inutile dégrade les performances et entraîne un risque d’interblocages et de conditions de concurrence.</span><span class="sxs-lookup"><span data-stu-id="0900f-191">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
-   <span data-ttu-id="0900f-192">Définissez les données static (`Shared` en Visual Basic) comme thread-safe par défaut.</span><span class="sxs-lookup"><span data-stu-id="0900f-192">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
-   <span data-ttu-id="0900f-193">Ne définissez pas les données d’instance comme thread-safe par défaut.</span><span class="sxs-lookup"><span data-stu-id="0900f-193">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="0900f-194">L’ajout de verrous pour créer un code thread-safe diminue les performances, multiplie les conflits de verrou et occasionne un risque d’interblocages.</span><span class="sxs-lookup"><span data-stu-id="0900f-194">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="0900f-195">Dans les modèles d’application communs, le code utilisateur n’est exécuté que par un seul thread à la fois, ce qui minimise la nécessité d’une cohérence de thread.</span><span class="sxs-lookup"><span data-stu-id="0900f-195">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="0900f-196">C’est la raison pour laquelle les bibliothèques de classes .NET Framework ne sont pas thread-safe par défaut.</span><span class="sxs-lookup"><span data-stu-id="0900f-196">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
-   <span data-ttu-id="0900f-197">Évitez de fournir des méthodes statiques qui modifient l’état statique.</span><span class="sxs-lookup"><span data-stu-id="0900f-197">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="0900f-198">Dans les scénarios de serveur courants, l’état statique est partagé entre les requêtes, ce qui signifie que plusieurs threads peuvent exécuter ce code en même temps.</span><span class="sxs-lookup"><span data-stu-id="0900f-198">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="0900f-199">Ceci occasionne un risque de bogues de threading.</span><span class="sxs-lookup"><span data-stu-id="0900f-199">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="0900f-200">Envisagez d’utiliser un modèle de conception qui encapsule les données dans des instances non partagées entre les requêtes.</span><span class="sxs-lookup"><span data-stu-id="0900f-200">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="0900f-201">En outre, si les données static sont synchronisées, les appels entre les méthodes statiques qui modifient l’état peuvent entraîner des interblocages ou une synchronisation redondante et dégrader ainsi les performances.</span><span class="sxs-lookup"><span data-stu-id="0900f-201">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0900f-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0900f-202">See Also</span></span>  
 [<span data-ttu-id="0900f-203">Thread</span><span class="sxs-lookup"><span data-stu-id="0900f-203">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="0900f-204">Threads et threading</span><span class="sxs-lookup"><span data-stu-id="0900f-204">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
