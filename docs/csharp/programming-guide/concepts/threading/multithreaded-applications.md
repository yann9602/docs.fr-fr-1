---
title: Applications multithread (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: b7015cfb-d506-4eac-b2f8-b2caaa9cc977
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dfe0f9c6e911295270df8464d1070a524412466d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="multithreaded-applications-c"></a><span data-ttu-id="34d89-102">Applications multithread (C#)</span><span class="sxs-lookup"><span data-stu-id="34d89-102">Multithreaded Applications (C#)</span></span>
<span data-ttu-id="34d89-103">Avec C#, vous pouvez écrire des applications qui effectuent plusieurs tâches en même temps.</span><span class="sxs-lookup"><span data-stu-id="34d89-103">With C#, you can write applications that perform multiple tasks at the same time.</span></span> <span data-ttu-id="34d89-104">Les tâches présentant le risque d’accaparer les ressources d’autres tâches peuvent s’exécuter sur des threads distincts : ce processus est appelé *multithreading* ou *threading libre*.</span><span class="sxs-lookup"><span data-stu-id="34d89-104">Tasks with the potential of holding up other tasks can execute on separate threads, a process known as *multithreading* or *free threading*.</span></span>  
  
 <span data-ttu-id="34d89-105">Les applications qui utilisent le multithreading sont plus réactives aux entrées utilisateur, car l’interface utilisateur reste active pendant que les tâches sollicitant beaucoup le processeur s’exécutent sur des threads distincts.</span><span class="sxs-lookup"><span data-stu-id="34d89-105">Applications that use multithreading are more responsive to user input because the user interface stays active as processor-intensive tasks execute on separate threads.</span></span> <span data-ttu-id="34d89-106">Le multithreading est également utile quand vous créez des applications scalables, car vous pouvez ajouter des threads au fil de l’augmentation de la charge de travail.</span><span class="sxs-lookup"><span data-stu-id="34d89-106">Multithreading is also useful when you create scalable applications, because you can add threads as the workload increases.</span></span>  
  
## <a name="creating-and-using-threads"></a><span data-ttu-id="34d89-107">Création et utilisation des threads</span><span class="sxs-lookup"><span data-stu-id="34d89-107">Creating and Using Threads</span></span>  
 <span data-ttu-id="34d89-108">Si vous avez besoin plus de contrôle sur le comportement des threads de votre application, vous pouvez gérer vous-même les threads.</span><span class="sxs-lookup"><span data-stu-id="34d89-108">If you need more control over the behavior of your application's threads, you can manage the threads yourself.</span></span> <span data-ttu-id="34d89-109">Notez cependant que l’écriture d’applications multithreads correctes peut être difficile : votre application peut cesser de répondre ou rencontrer des erreurs transitoires dues aux conditions de concurrence.</span><span class="sxs-lookup"><span data-stu-id="34d89-109">However, realize that writing correct multithreaded applications can be difficult: Your application may stop responding or experience transient errors caused by race conditions.</span></span> <span data-ttu-id="34d89-110">Pour plus d’informations, consultez [Composants thread-safe](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).</span><span class="sxs-lookup"><span data-stu-id="34d89-110">For more information, see [Thread-Safe Components](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).</span></span>  
  
 <span data-ttu-id="34d89-111">Pour créer un thread, vous devez déclarer une variable de type <xref:System.Threading.Thread> et appeler le constructeur, en fournissant le nom de la procédure ou de la méthode que vous voulez exécuter sur le nouveau thread.</span><span class="sxs-lookup"><span data-stu-id="34d89-111">You create a new thread by declaring a variable of type <xref:System.Threading.Thread> and calling the constructor, providing the name of the procedure or method that you want to execute on the new thread.</span></span> <span data-ttu-id="34d89-112">Le code suivant fournit un exemple.</span><span class="sxs-lookup"><span data-stu-id="34d89-112">The following code provides an example.</span></span>  
  
```csharp  
System.Threading.Thread newThread =  
    new System.Threading.Thread(AMethod);  
```  
  
### <a name="starting-and-stopping-threads"></a><span data-ttu-id="34d89-113">Démarrage et arrêt des threads</span><span class="sxs-lookup"><span data-stu-id="34d89-113">Starting and Stopping Threads</span></span>  
 <span data-ttu-id="34d89-114">Pour lancer l’exécution d’un nouveau thread, utilisez la méthode <xref:System.Threading.Thread.Start%2A>, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="34d89-114">To start the execution of a new thread, use the <xref:System.Threading.Thread.Start%2A> method, as shown in the following code.</span></span>  
  
```csharp  
newThread.Start();  
```  
  
 <span data-ttu-id="34d89-115">Pour arrêter l’exécution d’un thread, utilisez la méthode <xref:System.Threading.Thread.Abort%2A>, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="34d89-115">To stop the execution of a thread, use the <xref:System.Threading.Thread.Abort%2A> method, as shown in the following code.</span></span>  
  
```csharp  
newThread.Abort();  
```  
  
 <span data-ttu-id="34d89-116">En plus de démarrer et d’arrêter les threads, vous pouvez aussi les suspendre en appelant la méthode <xref:System.Threading.Thread.Sleep%2A> ou <xref:System.Threading.Thread.Suspend%2A>, reprendre un thread suspendu à l’aide de la méthode <xref:System.Threading.Thread.Resume%2A> et détruire un thread à l’aide de la méthode <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="34d89-116">Besides starting and stopping threads, you can also pause threads by calling the <xref:System.Threading.Thread.Sleep%2A> or <xref:System.Threading.Thread.Suspend%2A> method, resume a suspended thread by using the <xref:System.Threading.Thread.Resume%2A> method, and destroy a thread by using the <xref:System.Threading.Thread.Abort%2A> method</span></span>  
  
### <a name="thread-methods"></a><span data-ttu-id="34d89-117">Méthodes pour les threads</span><span class="sxs-lookup"><span data-stu-id="34d89-117">Thread Methods</span></span>  
 <span data-ttu-id="34d89-118">Le tableau suivant répertorie certaines des méthodes que vous pouvez utiliser pour contrôler des threads individuels.</span><span class="sxs-lookup"><span data-stu-id="34d89-118">The following table shows some of the methods that you can use to control individual threads.</span></span>  
  
|<span data-ttu-id="34d89-119">Méthode</span><span class="sxs-lookup"><span data-stu-id="34d89-119">Method</span></span>|<span data-ttu-id="34d89-120">Action</span><span class="sxs-lookup"><span data-stu-id="34d89-120">Action</span></span>|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|<span data-ttu-id="34d89-121">Démarre l’exécution d’un thread.</span><span class="sxs-lookup"><span data-stu-id="34d89-121">Causes a thread to start to run.</span></span>|  
|<xref:System.Threading.Thread.Sleep%2A>|<span data-ttu-id="34d89-122">Suspend un thread pendant une durée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34d89-122">Pauses a thread for a specified time.</span></span>|  
|<xref:System.Threading.Thread.Suspend%2A>|<span data-ttu-id="34d89-123">Suspend un thread quand celui-ci atteint un point sécurisé.</span><span class="sxs-lookup"><span data-stu-id="34d89-123">Pauses a thread when it reaches a safe point.</span></span>|  
|<xref:System.Threading.Thread.Abort%2A>|<span data-ttu-id="34d89-124">Arrête un thread quand celui-ci atteint un point sécurisé.</span><span class="sxs-lookup"><span data-stu-id="34d89-124">Stops a thread when it reaches a safe point.</span></span>|  
|<xref:System.Threading.Thread.Resume%2A>|<span data-ttu-id="34d89-125">Redémarre un thread suspendu.</span><span class="sxs-lookup"><span data-stu-id="34d89-125">Restarts a suspended thread</span></span>|  
|<xref:System.Threading.Thread.Join%2A>|<span data-ttu-id="34d89-126">Force le thread actif à attendre qu’un autre thread se termine.</span><span class="sxs-lookup"><span data-stu-id="34d89-126">Causes the current thread to wait for another thread to finish.</span></span> <span data-ttu-id="34d89-127">Si elle est utilisée avec une valeur de délai d’attente, cette méthode retourne `True` si le thread se termine dans le délai imparti.</span><span class="sxs-lookup"><span data-stu-id="34d89-127">If used with a time-out value, this method returns `True` if the thread finishes in the allocated time.</span></span>|  
  
### <a name="safe-points"></a><span data-ttu-id="34d89-128">Points sécurisés</span><span class="sxs-lookup"><span data-stu-id="34d89-128">Safe Points</span></span>  
 <span data-ttu-id="34d89-129">L’action de la plupart de ces méthodes est explicite, mais le concept de *points sécurisés* est peut être nouveau pour vous.</span><span class="sxs-lookup"><span data-stu-id="34d89-129">Most of these methods are self-explanatory, but the concept of *safe points* may be new to you.</span></span> <span data-ttu-id="34d89-130">Les points sécurisés sont des endroits dans le code où le common language runtime peut effectuer sans risque une opération de *garbage collection*, qui est le processus consistant à libérer les variables inutilisées et à libérer la mémoire.</span><span class="sxs-lookup"><span data-stu-id="34d89-130">Safe points are locations in code where it is safe for the common language runtime to perform automatic *garbage collection*, the process of releasing unused variables and reclaiming memory.</span></span> <span data-ttu-id="34d89-131">Quand vous appelez la méthode <xref:System.Threading.Thread.Abort%2A> ou <xref:System.Threading.Thread.Suspend%2A> d’un thread, le common language runtime analyse le code et détermine l’emplacement approprié pour arrêter l’exécution d’un thread.</span><span class="sxs-lookup"><span data-stu-id="34d89-131">When you call the <xref:System.Threading.Thread.Abort%2A> or <xref:System.Threading.Thread.Suspend%2A> method of a thread, the common language runtime analyzes the code and determines the location of an appropriate location for the thread to stop running.</span></span>  
  
### <a name="thread-properties"></a><span data-ttu-id="34d89-132">Propriétés du thread</span><span class="sxs-lookup"><span data-stu-id="34d89-132">Thread Properties</span></span>  
 <span data-ttu-id="34d89-133">Les threads contiennent également plusieurs propriétés utiles, qui sont répertoriées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="34d89-133">Threads also contain several useful properties, as shown in the following table:</span></span>  
  
|<span data-ttu-id="34d89-134">Propriété</span><span class="sxs-lookup"><span data-stu-id="34d89-134">Property</span></span>|<span data-ttu-id="34d89-135">Valeur</span><span class="sxs-lookup"><span data-stu-id="34d89-135">Value</span></span>|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|<span data-ttu-id="34d89-136">Contient la valeur `True` si un thread est actif.</span><span class="sxs-lookup"><span data-stu-id="34d89-136">Contains the value `True` if a thread is active.</span></span>|  
|<xref:System.Threading.Thread.IsBackground%2A>|<span data-ttu-id="34d89-137">Obtient ou définit une valeur booléenne qui indique si un thread est ou doit être un thread d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="34d89-137">Gets or sets a Boolean that indicates if a thread is or should be a background thread.</span></span> <span data-ttu-id="34d89-138">Les threads d’arrière-plan ressemblent aux threads de premier plan, excepté qu’un thread d’arrière-plan n’empêche pas un processus de s’arrêter.</span><span class="sxs-lookup"><span data-stu-id="34d89-138">Background threads are like foreground threads, but a background thread does not prevent a process from stopping.</span></span> <span data-ttu-id="34d89-139">Une fois que tous les threads de premier plan appartenant à un processus sont arrêtés, le common language runtime met fin au processus en appelant la méthode <xref:System.Threading.Thread.Abort%2A> sur les threads d’arrière-plan encore actifs.</span><span class="sxs-lookup"><span data-stu-id="34d89-139">Once all foreground threads that belong to a process have stopped, the common language runtime ends the process by calling the <xref:System.Threading.Thread.Abort%2A> method on background threads that are still alive.</span></span>|  
|<xref:System.Threading.Thread.Name%2A>|<span data-ttu-id="34d89-140">Obtient ou définit le nom d’un thread.</span><span class="sxs-lookup"><span data-stu-id="34d89-140">Gets or sets the name of a thread.</span></span> <span data-ttu-id="34d89-141">Généralement utilisé pour découvrir des threads individuels lors du débogage.</span><span class="sxs-lookup"><span data-stu-id="34d89-141">Most frequently used to discover individual threads when you debug.</span></span>|  
|<xref:System.Threading.Thread.Priority%2A>|<span data-ttu-id="34d89-142">Obtient ou définit une valeur qui est utilisée par le système d’exploitation pour classer par priorité la planification des threads.</span><span class="sxs-lookup"><span data-stu-id="34d89-142">Gets or sets a value that is used by the operating system to prioritize thread scheduling.</span></span>|  
|<xref:System.Threading.Thread.ThreadState%2A>|<span data-ttu-id="34d89-143">Contient une valeur qui décrit le ou les états d’un thread.</span><span class="sxs-lookup"><span data-stu-id="34d89-143">Contains a value that describes a thread's state or states.</span></span>|  
  
## <a name="thread-priorities"></a><span data-ttu-id="34d89-144">Priorités des threads</span><span class="sxs-lookup"><span data-stu-id="34d89-144">Thread Priorities</span></span>  
 <span data-ttu-id="34d89-145">Chaque thread a une propriété priority, qui détermine la taille d’un intervalle de temps processeur pendant lequel il doit s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="34d89-145">Every thread has a priority property that determines how big or small a slice of processor time it has to execute.</span></span> <span data-ttu-id="34d89-146">Le système d’exploitation alloue des intervalles de temps plus longs aux threads à priorité élevée, et des intervalles de temps plus courts pour les threads de priorité basse.</span><span class="sxs-lookup"><span data-stu-id="34d89-146">The operating system allocates longer time slices to high-priority threads and shorter time slices to low-priority threads.</span></span> <span data-ttu-id="34d89-147">Les nouveaux threads sont créés avec la valeur `Normal`, mais vous pouvez remplacer la valeur de la propriété <xref:System.Threading.Thread.Priority%2A> par n’importe quelle valeur contenue dans l’énumération <xref:System.Threading.ThreadPriority>.</span><span class="sxs-lookup"><span data-stu-id="34d89-147">New threads are created with the value of `Normal`, but you can change the <xref:System.Threading.Thread.Priority%2A> property to any value in the <xref:System.Threading.ThreadPriority> enumeration.</span></span>  
  
 <span data-ttu-id="34d89-148">Consultez <xref:System.Threading.ThreadPriority> pour obtenir une description détaillée des différentes priorités de thread.</span><span class="sxs-lookup"><span data-stu-id="34d89-148">See <xref:System.Threading.ThreadPriority> for a detailed description of the various thread priorities.</span></span>  
  
## <a name="foreground-and-background-threads"></a><span data-ttu-id="34d89-149">Threads de premier plan et d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="34d89-149">Foreground and Background Threads</span></span>  
 <span data-ttu-id="34d89-150">Un *thread de premier plan* peut s’exécuter indéfiniment, tandis qu’un *thread d’arrière-plan* s’arrête dès que le dernier thread de premier plan s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="34d89-150">A *foreground thread* runs indefinitely, whereas a *background thread* stops as soon as the last foreground thread has stopped.</span></span> <span data-ttu-id="34d89-151">Vous pouvez utiliser la propriété <xref:System.Threading.Thread.IsBackground%2A> pour déterminer ou modifier l’état d’arrière-plan d’un thread.</span><span class="sxs-lookup"><span data-stu-id="34d89-151">You can use the <xref:System.Threading.Thread.IsBackground%2A> property to determine or change the background status of a thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d89-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34d89-152">See Also</span></span>  
 <span data-ttu-id="34d89-153"><xref:System.Threading.Thread></span><span class="sxs-lookup"><span data-stu-id="34d89-153"><xref:System.Threading.Thread></span></span>   
 <span data-ttu-id="34d89-154">[Synchronisation des threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="34d89-154">[Thread Synchronization (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
 <span data-ttu-id="34d89-155">[Paramètres et valeurs de retour pour les procédures multithread (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="34d89-155">[Parameters and Return Values for Multithreaded Procedures (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span></span>  
 [<span data-ttu-id="34d89-156">Threading (C#)</span><span class="sxs-lookup"><span data-stu-id="34d89-156">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)

