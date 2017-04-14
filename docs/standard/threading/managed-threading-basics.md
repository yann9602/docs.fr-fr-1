---
title: "Managed Threading Basics | Microsoft Docs"
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
  - "multiple threads"
  - "threading [.NET Framework], multiple threads"
  - "threading [.NET Framework], about threading"
  - "managed threading"
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Managed Threading Basics
Les cinq premières rubriques de cette section sont destinées à vous aider à déterminer les scénarios où vous devez utiliser le threading managé, et à expliquer certaines fonctionnalités de base.  Pour plus d'informations sur les classes qui fournissent des fonctionnalités supplémentaires, consultez [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) et [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Les autres rubriques dans cette section portent sur des rubriques avancées, y compris l'interaction du threading managé avec le système d'exploitation Windows.  
  
> [!NOTE]
>  Dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la bibliothèque parallèle de tâches et PLINQ fournissent des API pour le parallélisme des tâches et des données dans les programmes multithreads.  Pour plus d'informations, consultez [Parallel Programming](../../../docs/standard/parallel-programming/index.md).  
  
## Dans cette section  
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)  
 Explique les avantages et inconvénients de plusieurs threads et présente les scénarios dans lesquels vous pouvez créer des threads ou utiliser des threads de pool.  
  
 [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Décrit le comportement des exceptions non gérées dans les threads pour les différentes versions du .NET Framework, en particulier les situations au cours desquelles elles finissent par arrêter l'application.  
  
 [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Décrit les stratégies de synchronisation des données dans des classes qui seront utilisées avec plusieurs threads.  
  
 [États des threads managés](../../../docs/standard/threading/managed-thread-states.md)  
 Décrit les états de thread de base et explique comment détecter si un thread s'exécute ou non.  
  
 [Foreground and Background Threads](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Explique les différences entre les threads de premier plan et d'arrière\-plan.  
  
 [Managed and Unmanaged Threading in Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Explique la relation entre le threading managé et non managé, répertorie les équivalents managés pour les API de threading Windows, et explique l'interaction des apartments \(cloisonnés\) COM et des threads managés.  
  
 [Thread.Suspend, Garbage Collection, and Safe Points](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 Décrit l'interruption de thread et le garbage collection.  
  
 [Thread Local Storage: Thread\-Relative Static Fields and Data Slots](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Décrit les mécanismes de stockage relatifs à un thread.  
  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 Décrit comment des operations asynchrone ou longue et synchrones peuvent être annulées en utilisant un jeton d'annulation.  
  
## Référence  
 <xref:System.Threading.Thread>  
 Fournit une documentation de référence pour la classe **Thread**, qui représente un thread managé, que celle\-ci provienne du code non managé ou qu'elle ait été créée dans une application managée.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Offre un moyen sûr d'implémenter le multithreading conjointement avec des objets interface utilisateur.  
  
## Rubriques connexes  
 [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Décrit les classes managées utilisées pour synchroniser les activités de plusieurs threads.  
  
 [Managed Threading Best Practices](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Décrit des problèmes courants associés au multithreading et les stratégies permettant de les éviter.  
  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)  
 Décrit la bibliothèque parallèle de tâches et PLINQ, lesquels simplifient considérablement la création d'applications .NET Framework asynchrones et multithreads.