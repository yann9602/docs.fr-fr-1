---
title: "Overview of Synchronization Primitives | Microsoft Docs"
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
  - "synchronization, threads"
  - "threading [.NET Framework],synchronizing threads"
  - "managed threading"
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Overview of Synchronization Primitives
Le .NET Framework fournit une plage de primitives de synchronisation pour contrôler les interactions de threads et éviter des conditions de concurrence.  Celles\-ci peuvent être divisées approximativement en trois catégories : le verrouillage, la signalisation et les opérations verrouillées.  
  
 Les catégories ne sont pas clairement définies : certains mécanismes de synchronisation possèdent des caractéristiques relevant de plusieurs catégories. Les événements qui libèrent un seul thread à la fois sont similaires à des verrous d’un point de vue fonctionnel. La libération d'un verrou quelconque peut être considérée comme un signal et les opérations verrouillées peuvent être utilisées pour construire des verrous.  Toutefois, ces catégories restent utiles.  
  
 Il est important de se rappeler que la synchronisation de threads est coopérative.  Si un seul thread ignore un mécanisme de synchronisation et accède directement à la ressource protégée, ce mécanisme de synchronisation ne peut pas être efficace.  
  
 Cette vue d'ensemble contient les sections suivantes :  
  
-   [Verrouillage](#locking)  
  
-   [Signaling](#signaling)  
  
-   [Types de synchronisation légers](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Opérations verrouillées](#interlocked_operations)  
  
<a name="locking"></a>   
## Verrouillage  
 Les verrous donnent le contrôle d'une ressource à un seul thread à la fois ou à un nombre spécifié de threads.  Un thread qui demande un verrou exclusif alors que ce verrou est en cours d'utilisation se bloque jusqu'à ce que le verrou soit de nouveau disponible.  
  
### Verrous exclusifs  
 La forme la plus simple de verrouillage est l’instruction C\# `lock` \(`SyncLock` en Visual Basic\), qui contrôle l'accès à un bloc de code.  Ce type de bloc est souvent appelé « section critique ».  L’instruction `lock` est implémentée à l'aide des méthodes <xref:System.Threading.Monitor.Enter%2A> et <xref:System.Threading.Monitor.Exit%2A> de la classe <xref:System.Threading.Monitor>, et elle utilise `try…catch…finally` pour garantir la libération du verrou.  
  
 En général, l’utilisation de l’instruction `lock` pour protéger de petits blocs de code, sans jamais englober plus d'une méthode, représente la meilleure façon d'utiliser la classe <xref:System.Threading.Monitor>.  Bien que puissante, la classe <xref:System.Threading.Monitor> est susceptible de rendre orphelins des verrous et des blocages.  
  
#### Classe Monitor  
 La classe <xref:System.Threading.Monitor> fournit des fonctionnalités supplémentaires, qui peuvent être utilisée conjointement à l’instruction `lock` :  
  
-   La méthode <xref:System.Threading.Monitor.TryEnter%2A> autorise un thread qui est bloqué en attente d’une ressource d'abandonner après un intervalle spécifié.  Elle retourne une valeur booléenne qui indique la réussite ou l'échec, et qui peut être utilisée pour détecter et éviter des blocages potentiels.  
  
-   La méthode <xref:System.Threading.Monitor.Wait%2A> est appelée par un thread dans une section critique.  Elle abandonne le contrôle de la ressource et se bloque jusqu'à ce que la ressource soit de nouveau disponible.  
  
-   Les méthodes <xref:System.Threading.Monitor.Pulse%2A> et <xref:System.Threading.Monitor.PulseAll%2A> autorisent un thread en passe de libérer le verrou ou d'appeler la méthode <xref:System.Threading.Monitor.Wait%2A> à placer un ou plusieurs threads dans la file d'attente opérationnelle, afin qu'ils puissent acquérir le verrou.  
  
 Les dépassements de délai sur les surcharges de la méthode <xref:System.Threading.Monitor.Wait%2A> permettent aux threads en attente de revenir à la file d'attente opérationnelle.  
  
 La classe <xref:System.Threading.Monitor> peut permettre un verrouillage dans plusieurs domaines d'application si l'objet utilisé comme verrou dérive de <xref:System.MarshalByRefObject>.  
  
 <xref:System.Threading.Monitor> possède l’affinité de thread.  Autrement dit, un thread entré dans le moniteur doit sortir en appelant <xref:System.Threading.Monitor.Exit%2A> ou <xref:System.Threading.Monitor.Wait%2A>.  
  
 Il est impossible d’instancier la classe <xref:System.Threading.Monitor>.  Ses méthodes sont statiques \(`Shared` en Visual Basic\) et agissent sur un objet verrou instanciable.  
  
 Pour bénéficier d’une vue d'ensemble conceptuelle, consultez [Moniteurs](../Topic/Monitors.md).  
  
#### Mutex, classe  
 Les threads demandent un <xref:System.Threading.Mutex> en appelant une surcharge de sa méthode <xref:System.Threading.WaitHandle.WaitOne%2A>.  Des surcharges avec délais d'attente sont fournies, afin de permettre aux threads d'abandonner l'attente.  À la différence de la classe <xref:System.Threading.Monitor>, un mutex peut être local ou global.  Les mutex globaux, appelés également mutex nommés, sont visibles dans tout le système d'exploitation et peuvent être utilisés pour synchroniser des threads dans plusieurs domaines d'application ou processus.  Les mutex locaux dérivent de <xref:System.MarshalByRefObject> et peuvent être utilisés au\-delà des limites des domaines d'application.  
  
 Par ailleurs, <xref:System.Threading.Mutex> dérive de <xref:System.Threading.WaitHandle>, ce qui signifie qu'il peut être utilisé avec les mécanismes de signalisation fournis par <xref:System.Threading.WaitHandle>, tels que les méthodes <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A> et <xref:System.Threading.WaitHandle.SignalAndWait%2A>.  
  
 À l’instar de <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> possède l'affinité de thread.  Contrairement à <xref:System.Threading.Monitor>, il est possible d’instancier un objet <xref:System.Threading.Mutex>.  
  
 Pour bénéficier d’une vue d'ensemble conceptuelle, consultez [Mutexes](../../../docs/standard/threading/mutexes.md).  
  
#### Classe SpinLock  
 À partir du [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez utiliser la classe <xref:System.Threading.SpinLock> quand la charge mémoire requise par <xref:System.Threading.Monitor> dégrade les performances.  Quand <xref:System.Threading.SpinLock> rencontre une section critique verrouillée, il tourne simplement en boucle jusqu'à ce que le verrou soit de nouveau disponible.  Si le verrou est maintenu très peu de temps, la rotation peut fournir de meilleures performances que le blocage.  Toutefois, si le verrou est maintenu pendant plusieurs dizaines de cycles, <xref:System.Threading.SpinLock> fonctionne aussi bien que <xref:System.Threading.Monitor>, mais utilise plus de cycles processeur et peut donc dégrader les performances d'autres threads ou processus.  
  
### Autres verrous  
 Les verrous n'ont pas besoin d'être exclusifs.  Il est souvent utile d'autoriser un nombre limité d’accès simultanés de threads à une ressource.  Les sémaphores et les verrous de lecteur\-writer sont conçus pour contrôler ce type d'accès à des ressources regroupées.  
  
#### Classe ReaderWriterLock  
 La classe <xref:System.Threading.ReaderWriterLockSlim> est utile dans le cas où un thread qui modifie des données, le writer, doit disposer d’un accès exclusif à une ressource.  Quand le writer n'est pas actif, un nombre quelconque de lecteurs peuvent accéder à la ressource \(par exemple, en appelant la méthode <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A>\).  Quand un thread demande un accès exclusif \(par exemple, en appelant la méthode <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A>\), les demandes suivantes des lecteurs sont bloquées jusqu'à ce que tous les lecteurs existants aient libéré le verrou et que le writer ait acquis et libéré le verrou.  
  
 <xref:System.Threading.ReaderWriterLockSlim> possède l’affinité de thread.  
  
 Pour une vue d'ensemble conceptuelle, consultez [Reader\-Writer Locks](../../../docs/standard/threading/reader-writer-locks.md).  
  
#### Semaphore, classe  
 La classe <xref:System.Threading.Semaphore> permet à un nombre spécifié de threads d'accéder à une ressource.  Les autres threads qui demandent la ressource sont bloqués jusqu'à ce qu'un thread libère le sémaphore.  
  
 À l’instar de la classe <xref:System.Threading.Mutex>, <xref:System.Threading.Semaphore> dérive de <xref:System.Threading.WaitHandle>.  De plus, comme <xref:System.Threading.Mutex>, un <xref:System.Threading.Semaphore> peut être local ou global.  Il peut être utilisé au\-delà des limites des domaines d'application.  
  
 Contrairement à <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> et <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Semaphore> ne possède pas l’affinité de thread.  Cela signifie qu'il peut être utilisé dans des scénarios où un thread acquiert le sémaphore et un autre le libère.  
  
 Pour bénéficier d’une vue d'ensemble conceptuelle, consultez [Semaphore and SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=fullName> est un sémaphore léger pour la synchronisation dans la limite d’un processus unique.  
  
 [Retour au début](#top)  
  
<a name="signaling"></a>   
## Signaling  
 La façon la plus simple d’attendre un signal d'un autre thread consiste à appeler la méthode <xref:System.Threading.Thread.Join%2A>, qui se bloque jusqu'à ce que l'autre thread se termine.  <xref:System.Threading.Thread.Join%2A> a deux surcharges qui autorisent le thread bloqué à abandonner l'attente après un intervalle spécifié.  
  
 Les handles d'attente fournissent un ensemble beaucoup plus riche de fonctions d'attente et de signalisation.  
  
### Handles d'attente  
 Les handles d'attente dérivent de la classe <xref:System.Threading.WaitHandle>, qui, elle\-même, dérive de <xref:System.MarshalByRefObject>.  Par conséquent, les handles d'attente peuvent être utilisés pour synchroniser les activités des threads au\-delà des limites des domaines d'application.  
  
 Les threads se bloquent sur les handles d’attente en appelant la méthode d'instance <xref:System.Threading.WaitHandle.WaitOne%2A> ou l'une des méthodes statiques <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A> ou <xref:System.Threading.WaitHandle.SignalAndWait%2A>.  La façon dont ils sont libérés dépend de la méthode appelée et du type de handles d'attente.  
  
 Pour bénéficier d’une vue d'ensemble conceptuelle, consultez [Wait Handles](../Topic/Wait%20Handles.md).  
  
#### Handles d'attente d'événement  
 Les handles d'attente d'événement incluent la classe <xref:System.Threading.EventWaitHandle> et ses classes dérivées <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.ManualResetEvent>.  Les threads sont libérés d'un handle d'attente d'événement quand ce dernier en reçoit le signal par l’appel à sa méthode <xref:System.Threading.EventWaitHandle.Set%2A> ou à l'aide de la méthode <xref:System.Threading.WaitHandle.SignalAndWait%2A>.  
  
 Les handles d’attente d’événement se réinitialisent automatiquement, à l’instar d’un tourniquet qui permet le passage d’un seul thread à chaque signal reçu, ou ils doivent être réinitialisés manuellement, comme une barrière qui reste fermée jusqu'à la réception d’un signal d’ouverture, puis reste ouverte jusqu'à ce que quelqu'un la ferme.  Comme leurs noms l'indiquent, <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.ManualResetEvent> représentent le premier et le second type de réinitialisation, respectivement.  <xref:System.Threading.ManualResetEventSlim?displayProperty=fullName> est un événement léger pour la synchronisation dans une limite de processus unique.  
  
 <xref:System.Threading.EventWaitHandle> peut représenter les deux types d'événement et peut être local ou global.  Les classes dérivées <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.ManualResetEvent> sont toujours locales.  
  
 Les handles d'attente d'événement n'ont pas d'affinité de thread.  Un thread quelconque peut envoyer un signal à un handle d'attente d'événement.  
  
 Pour bénéficier d’une vue d'ensemble conceptuelle, consultez [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
#### Classes Mutex et Semaphore  
 Comme les classes <xref:System.Threading.Mutex> et <xref:System.Threading.Semaphore> dérivent de <xref:System.Threading.WaitHandle>, elles peuvent être utilisées avec les méthodes statiques de <xref:System.Threading.WaitHandle>.  Par exemple, un thread peut utiliser la méthode <xref:System.Threading.WaitHandle.WaitAll%2A> pour attendre que les trois conditions suivantes soient vraies : <xref:System.Threading.EventWaitHandle> est signalé, <xref:System.Threading.Mutex> est libéré et <xref:System.Threading.Semaphore> est libéré.  De même, un thread peut utiliser la méthode <xref:System.Threading.WaitHandle.WaitAny%2A> pour attendre que l'une de ces conditions soit vraie.  
  
 Pour <xref:System.Threading.Mutex> ou <xref:System.Threading.Semaphore>, recevoir un signal signifie être libéré.  Si l’un des deux types est utilisé comme premier argument de la méthode <xref:System.Threading.WaitHandle.SignalAndWait%2A>, il est libéré.  Dans le cas de <xref:System.Threading.Mutex>, qui possède l’affinité de thread, une exception est levée si le thread appelant n’est pas propriétaire du mutex.  Comme mentionné précédemment, les sémaphores n'ont pas d'affinité de thread.  
  
#### Cloisonnement  
 La classe <xref:System.Threading.Barrier> permet de synchroniser plusieurs threads cycliquement afin qu'ils se bloquent tous au même point et attendent que tous les autres threads soient terminés.  Le cloisonnement est utile quand un ou plusieurs threads requièrent les résultats d'un autre thread avant de passer à la phase suivante d'un algorithme.  Pour plus d'informations, consultez [Barrier](../../../docs/standard/threading/barrier.md).  
  
 [Retour au début](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## Types de synchronisation légers  
 À partir du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], vous pouvez utiliser des primitives de synchronisation qui fournissent des performances rapides en évitant une dépendance complexe sur les objets de noyau Win32, tels que les handles d'attente, chaque fois que possible.  En général, vous devez utiliser ces types quand les temps d'attente sont courts et uniquement lorsque les types de synchronisation d'origine ont été essayés et ont donné des résultats non satisfaisants.  Les types légers ne peuvent pas être utilisés dans les scénarios qui requièrent une communication interprocessus.  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=fullName> est une version légère de <xref:System.Threading.Semaphore?displayProperty=fullName>.  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=fullName> est une version légère de <xref:System.Threading.ManualResetEvent?displayProperty=fullName>.  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=fullName> représente un événement signalé quand son nombre est égal à zéro.  
  
-   <xref:System.Threading.Barrier?displayProperty=fullName> permet à plusieurs threads de se synchroniser les uns avec les autres sans nécessiter le contrôle d'un thread principal.  Un cloisonnement empêche chaque thread de continuer jusqu'à ce que tous les threads aient atteint un point spécifié.  
  
 [Retour au début](#top)  
  
<a name="spinwait"></a>   
## SpinWait  
 À partir du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], vous pouvez utiliser la structure <xref:System.Threading.SpinWait?displayProperty=fullName> quand un thread doit attendre le signalement d'un événement ou la satisfaction d'une condition, mais quand le temps d'attente réel est supposé être inférieur à la latence requise, en utilisant un handle d'attente ou en bloquant le thread actuel.  À l'aide de <xref:System.Threading.SpinWait>, vous pouvez spécifier une courte période de rotation pendant l'attente, puis générer \(par exemple, en attente ou en veille\) uniquement si la condition n'a pas été remplie dans le délai spécifié.  
  
 [Retour au début](#top)  
  
<a name="interlocked_operations"></a>   
## Opérations verrouillées  
 Les opérations verrouillées sont de simples opérations atomiques exécutées dans un emplacement de mémoire par les méthodes statiques de la classe <xref:System.Threading.Interlocked>.  Ces opérations atomiques incluent l'addition, l’incrémentation et la décrémentation, l’échange et l’échange conditionnel en fonction d'une comparaison, ainsi que des opérations de lecture pour des valeurs 64 bits sur les plateformes 32 bits.  
  
> [!NOTE]
>  L’atomicité n’est garantie que dans le cadre d’opérations individuelles. Quand plusieurs opérations doivent être exécutées en tant qu'unité, un mécanisme de synchronisation plus grossier doit être utilisé.  
  
 Bien qu’aucune de ces opérations ne constitue un verrou ou un signal, elles peuvent être utilisées pour construire des verrous et des signaux.  Étant natives au système d'exploitation Windows, les opérations verrouillées sont extrêmement rapides.  
  
 Elles peuvent être utilisées avec des garanties de mémoire volatile pour écrire des applications qui proposent un accès simultané non bloquant puissant.  Toutefois, elles exigent une programmation de bas niveau sophistiquée et donc, dans la plupart des cas, les verrous simples constituent un choix plus adapté.  
  
 Pour bénéficier d’une vue d'ensemble conceptuelle, consultez [Interlocked Operations](../../../docs/standard/threading/interlocked-operations.md).  
  
## Voir aussi  
 [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)   
 [Moniteurs](../Topic/Monitors.md)   
 [Mutexes](../../../docs/standard/threading/mutexes.md)   
 [Semaphore and SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)   
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)   
 [Wait Handles](../Topic/Wait%20Handles.md)   
 [Interlocked Operations](../../../docs/standard/threading/interlocked-operations.md)   
 [Reader\-Writer Locks](../../../docs/standard/threading/reader-writer-locks.md)   
 [Barrier](../../../docs/standard/threading/barrier.md)   
 [SpinWait](../../../docs/standard/threading/spinwait.md)   
 [SpinLock](../../../docs/standard/threading/spinlock.md)