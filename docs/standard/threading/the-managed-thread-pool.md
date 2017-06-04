---
title: "The Managed Thread Pool | Microsoft Docs"
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
  - "thread pooling [.NET Framework]"
  - "thread pools [.NET Framework]"
  - "threading [.NET Framework], thread pool"
  - "threading [.NET Framework], pooling"
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
caps.latest.revision: 24
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 24
---
# The Managed Thread Pool
La classe <xref:System.Threading.ThreadPool> fournit à votre application un pool de threads de travail qui sont gérés par le système, ce qui vous permet de vous concentrer sur les tâches d'application plutôt que sur la gestion des threads.  Si vous avez des tâches courtes qui nécessitent un traitement en arrière\-plan, le pool de threads managés est un moyen simple de tirer parti de plusieurs threads.  Par exemple, avec [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] et versions ultérieures, vous pouvez créer des objets <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> qui effectuent des tâches asynchrones sur des threads du pool.  
  
> [!NOTE]
>  Dans [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)] et versions ultérieures, le débit du pool de threads a été considérablement amélioré dans trois domaines clés qui étaient considérés comme des goulots d'étranglement dans les versions précédentes de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] : la mise en file d'attente des tâches, la distribution des threads de pool et la distribution des threads de terminaison d'E\/S.  Pour utiliser cette fonctionnalité, votre application doit cibler [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] ou version ultérieure.  
  
 Pour les tâches d'arrière\-plan qui interagissent avec l'interface utilisateur, .NET Framework version 2.0 fournit également la classe <xref:System.ComponentModel.BackgroundWorker>, qui communique à l'aide d'événements déclenchés sur le thread d'interface utilisateur.  
  
 .NET Framework utilise des threads de pool pour de nombreux scénarios, y compris la terminaison d'E\/S asynchrones, les rappels Timer, les opérations d'attente inscrites, les appels de méthodes asynchrones utilisant des délégués et les connexions de sockets <xref:System.Net>.  
  
## Quand ne pas utiliser les threads de pool  
 Il existe plusieurs scénarios dans lesquels il est préférable de créer et de gérer vos propres threads au lieu d'utiliser des threads de pool :  
  
-   Si vous devez utiliser un thread de premier plan.  
  
-   Si un thread doit avoir une priorité particulière.  
  
-   Si vous avez des tâches qui entraînent le blocage du thread pendant une longue durée.  Le pool de threads possède un nombre maximal de threads. Un grand nombre de threads de pool bloqués pourrait donc empêcher le démarrage des tâches.  
  
-   Vous devez placer les threads dans un thread unique cloisonné.  Tous les threads <xref:System.Threading.ThreadPool> se trouvent dans le multithread cloisonné.  
  
-   Vous avez besoin d'une identité stable associée au thread ou avez besoin de dédier un thread à une tâche.  
  
## Caractéristiques du pool de threads  
 Les threads des pools de threads sont des threads d'arrière\-plan.  Voir [Foreground and Background Threads](../../../docs/standard/threading/foreground-and-background-threads.md).  Chaque thread utilise la taille de pile par défaut, s'exécute avec la priorité par défaut et se trouve dans le multithread cloisonné.  
  
 Il n'y a qu'un seul pool de threads par processus.  
  
### Exceptions dans les threads de pool  
 Les exceptions non gérées sur les threads de pool entraînent la fin du processus.  Il existe trois exceptions à cette règle :  
  
-   Une <xref:System.Threading.ThreadAbortException> est levée dans un thread de pool, car <xref:System.Threading.Thread.Abort%2A> a été appelé.  
  
-   Une <xref:System.AppDomainUnloadedException> est levée dans un thread de pool, car le domaine d'application est en cours de déchargement.  
  
-   Le common language runtime ou un processus hôte met fin au thread.  
  
 Pour plus d'informations, voir [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  Dans les versions 1.0 et 1.1 de .NET Framework, le common language runtime intercepte sans assistance les exceptions non gérées dans les threads de pool.  Cela peut endommager l'état de l'application et éventuellement provoquer le blocage des applications, ce qui peut être très difficile à déboguer.  
  
### Nombre maximal de threads dans un pool  
 Le nombre d'opérations pouvant être mises en file d'attente dans un pool de threads est limité uniquement par la mémoire disponible. Cependant, le pool de threads limite le nombre de threads pouvant être simultanément actifs dans le processus.  Dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] et versions ultérieures, la taille par défaut du pool de threads d'un processus dépend de plusieurs facteurs, dont la taille de l'espace d'adressage virtuel.  Un processus peut appeler la méthode <xref:System.Threading.ThreadPool.GetMaxThreads%2A> pour déterminer le nombre de threads.  
  
 Vous pouvez contrôler le nombre maximal de threads à l'aide des méthodes <xref:System.Threading.ThreadPool.GetMaxThreads%2A> et <xref:System.Threading.ThreadPool.SetMaxThreads%2A>.  
  
> [!NOTE]
>  Dans les versions 1.0 et 1.1 de .NET Framework, la taille du pool de threads ne peut pas être définie à partir de code managé.  Le code qui héberge le common language runtime peut définir la taille à l'aide de `CorSetMaxThreads`, défini dans mscoree.h.  
  
### Valeurs minimales d'un pool de threads  
 Le pool de threads fournit de nouveaux threads de travail ou des threads de terminaison d'E\/S à la demande jusqu'à ce qu'il atteigne la valeur minimale spécifiée pour chaque catégorie.  Vous pouvez utiliser la méthode <xref:System.Threading.ThreadPool.GetMinThreads%2A> pour obtenir ces valeurs minimales.  
  
> [!NOTE]
>  Quand la demande est faible, le nombre réel de threads du pool peut être inférieur aux valeurs minimales.  
  
 Quand une valeur minimale est atteinte, le pool de threads peut créer des threads supplémentaires ou attendre que certaines tâches soient terminées.  Dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] et versions ultérieures, le pool de threads crée et détruit des threads de travail pour optimiser le débit, qui est défini comme le nombre de tâches exécutées par unité de temps.  Un nombre trop bas de threads peut ne pas permettre une utilisation optimale des ressources disponibles, tandis qu'un nombre trop élevé de threads peut augmenter les conflits de ressources.  
  
> [!CAUTION]
>  Vous pouvez utiliser la méthode <xref:System.Threading.ThreadPool.SetMinThreads%2A> pour augmenter le nombre minimal de threads inactifs.  Toutefois, une augmentation non nécessaire de ces valeurs peut entraîner des problèmes de performances.  Si vous démarrez trop de tâches en même temps, celles\-ci seront lentes.  Dans la plupart des cas, le pool de threads sera plus performant avec son propre algorithme d'allocation de threads.  
  
## Ignorer les vérifications de sécurité  
 Le pool de threads fournit également les méthodes <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=fullName> et <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=fullName>.  Ces méthodes ne doivent être utilisées que si vous êtes certain que la pile de l'appelant n'a pas fait l'objet de vérifications de sécurité effectuées pendant l'exécution de la tâche mise en file d'attente.  <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> et <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> capturent la pile de l'appelant, qui est fusionnée avec la pile du thread de pool quand le thread commence à exécuter une tâche.  Si une vérification de sécurité est requise, la pile entière doit être vérifiée.  Même si elle garantit une sécurité, cette vérification a un impact sur les performances.  
  
## Utilisation du pool de threads  
 Dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] et versions ultérieures, le moyen le plus simple d'utiliser le pool de threads est d'utiliser la [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md).  Par défaut, les types de bibliothèque parallèle, tels que <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601>, utilisent des threads de pool pour exécuter des tâches.  Vous pouvez également utiliser le pool de threads en appelant <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> depuis du code managé \(ou `CorQueueUserWorkItem` depuis du code non managé\) et en passant un délégué <xref:System.Threading.WaitCallback> représentant la méthode qui effectue la tâche.  Une autre façon d'utiliser le pool de threads est de mettre en file d'attente des éléments de travail associés à une opération d'attente en utilisant la méthode <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=fullName> et en passant un <xref:System.Threading.WaitHandle> qui, quand il est signalé ou quand il a expiré, appelle la méthode représentée par le délégué <xref:System.Threading.WaitOrTimerCallback>.  Les threads de pool sont utilisés pour appeler les méthodes de rappel.  
  
## Exemples de pool de threads  
 Les exemples de code de cette section illustrent le pool de threads à l'aide de la classe <xref:System.Threading.Tasks.Task>, de la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> et de la méthode <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=fullName>.  
  
-   [Exécution de tâches asynchrones avec la bibliothèque parallèle de tâches](#TaskParallelLibrary)  
  
-   [Exécution de code asynchrone avec QueueUserWorkItem](#ExecuteCodeWithQUWI)  
  
-   [Fourniture de données de tâche pour QueueUserWorkItem](#TaskDataForQUWI)  
  
-   [Utilisation de RegisterWaitForSingleObject](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### Exécution de tâches asynchrones avec la bibliothèque parallèle de tâches  
 L'exemple suivant montre comment créer et utiliser un objet <xref:System.Threading.Tasks.Task> en appelant la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=fullName>.  Pour obtenir un exemple qui utilise la classe <xref:System.Threading.Tasks.Task%601> pour retourner une valeur à partir d'une tâche asynchrone, voir [How to: Return a Value from a Task](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### Exécution de code asynchrone avec QueueUserWorkItem  
 L'exemple suivant met en file d'attente une tâche très simple représentée par la méthode `ThreadProc`, à l'aide de la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### Fourniture de données de tâche pour QueueUserWorkItem  
 L'exemple de code suivant utilise la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> pour mettre en file d'attente une tâche et fournir les données de cette tâche.  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### Utilisation de RegisterWaitForSingleObject  
 L'exemple suivant illustre plusieurs fonctionnalités de threading.  
  
-   La mise en file d'attente d'une tâche en vue de son exécution par des threads <xref:System.Threading.ThreadPool>, avec la méthode <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A>.  
  
-   La signalisation d'une tâche à exécuter avec <xref:System.Threading.AutoResetEvent>.  Voir [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
-   La gestion des délais d'expiration et des signaux avec un délégué <xref:System.Threading.WaitOrTimerCallback>.  
  
-   L'annulation d'une tâche mise en file d'attente avec <xref:System.Threading.RegisteredWaitHandle>.  
  
 [!code-cpp[Conceptual.ThreadPool#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.ThreadPool#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source3.cs#3)]
 [!code-vb[Conceptual.ThreadPool#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source3.vb#3)]  
  
## Voir aussi  
 <xref:System.Threading.ThreadPool>   
 <xref:System.Threading.Tasks.Task>   
 <xref:System.Threading.Tasks.Task%601>   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [How to: Return a Value from a Task](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)   
 [E\/S sur fichier asynchrones](../../../docs/standard/io/e-s-sur-fichier-asynchrones.md)   
 [Timers](../../../docs/standard/threading/timers.md)