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
# <a name="threading-objects-and-features"></a>Fonctionnalités et objets de threading
.NET Framework fournit plusieurs objets permettant de créer et de gérer des applications multithread. Les threads managés sont représentés par la classe <xref:System.Threading.Thread>. La classe <xref:System.Threading.ThreadPool> permet de créer et de gérer facilement des tâches d'arrière-plan multithread. La classe <xref:System.ComponentModel.BackgroundWorker> permet la même chose pour les tâches qui interagissent avec l'interface utilisateur. La classe <xref:System.Threading.Timer> exécute des tâches en arrière-plan à intervalles réguliers.  
  
 De plus, plusieurs classes permettent de synchroniser des activités de threads, y compris les classes <xref:System.Threading.Semaphore> et <xref:System.Threading.EventWaitHandle> de .NET Framework version 2.0 et ultérieures. Les fonctionnalités de ces classes sont comparées dans la section [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Pool de threads managés](../../../docs/standard/threading/the-managed-thread-pool.md)  
 Décrit la classe **ThreadPool**, qui vous permet de demander à un thread d’exécuter une tâche sans avoir à gérer les threads vous-même.  
  
 [Minuteries](../../../docs/standard/threading/timers.md)  
 Explique comment utiliser une **minuterie** pour spécifier le délégué devant être appelé à une heure spécifique.  
  
 [Moniteurs](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 Explique comment utiliser la classe **Monitor** pour synchroniser l’accès à un membre ou pour créer vos propres types de gestion de threads.  
  
 [Descripteurs d’attente](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 Décrit la classe <xref:System.Threading.WaitHandle>, qui est la classe de base abstraite pour les handles d'attente d'événements, les mutex et les sémaphores et qui permet d'attendre plusieurs événements de synchronisation.  
  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 Décrit les handles d’attente d’événements managés qui sont utilisés pour synchroniser les activités de thread en signalant et en attendant des signaux.  
  
 [Mutex](../../../docs/standard/threading/mutexes.md)  
 Explique comment utiliser un <xref:System.Threading.Mutex> pour synchroniser l’accès à un objet ou pour créer vos propres mécanismes de synchronisation.  
  
 [Opérations verrouillées](../../../docs/standard/threading/interlocked-operations.md)  
 Explique comment utiliser la classe <xref:System.Threading.Interlocked> pour incrémenter ou décrémenter une valeur et la stocker dans une même opération atomique.  
  
 [Verrous de lecteur-writer](../../../docs/standard/threading/reader-writer-locks.md)  
 Définit un verrou qui implémente une sémantique à enregistreur unique/lecteurs multiples.  
  
 [Semaphore et SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 Décrit les objets <xref:System.Threading.Semaphore> et explique comment les utiliser pour contrôler l'accès aux ressources limitées.  
  
 [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Compare les fonctionnalités des classes .NET Framework fournies pour verrouiller et synchroniser les threads managés.  
  
 [Barrier](../../../docs/standard/threading/barrier.md)  
 Décrit les objets <xref:System.Threading.Barrier> qui implémentent le modèle de cloisonnement pour la coordination des threads dans les opérations planifiées.  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 Décrit <xref:System.Threading.SpinLock>, une alternative légère à la classe Monitor pour certains scénarios de bas niveau.  
  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 Décrit <xref:System.Threading.SpinWait>, une primitive de synchronisation de bas niveau qui exécute une attente active avant d'initialiser une attente basée sur le noyau.  
  
## <a name="reference"></a>Référence  
 <xref:System.Threading.Thread>  
 Fournit la documentation de référence pour la classe **Thread** qui représente un thread managé, qu’elle provienne de code non managé ou qu’elle ait été créée dans une application managée.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Permet aux tâches d’arrière-plan d’interagir avec l’interface utilisateur, en communiquant via des événements déclenchés sur le thread d’interface utilisateur.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [E/S sur fichier asynchrones](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Explique comment les ports de terminaison asynchrones d'E/S utilisent le pool de threads pour exiger un traitement uniquement quand une opération d'entrée/sortie est terminée.  
  
 [La bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Décrit l'approche recommandée pour la programmation multithread dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] et versions ultérieures.
