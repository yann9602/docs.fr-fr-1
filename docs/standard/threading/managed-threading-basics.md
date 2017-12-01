---
title: "Éléments fondamentaux du threading managé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62c207f6074e33813887c6903f5285ee72d14e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading-basics"></a>Éléments fondamentaux du threading managé
Les cinq premières rubriques de cette section sont conçues pour vous aider à déterminer quand utiliser le threading managé et expliquer certaines fonctionnalités de base. Pour plus d’informations sur les classes qui fournissent des fonctionnalités supplémentaires, consultez [fonctionnalités et objets de Threading](../../../docs/standard/threading/threading-objects-and-features.md) et [vue d’ensemble des Primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Le reste des rubriques de cette section traitent des rubriques avancées, y compris l’interaction du threading managé avec le système d’exploitation Windows.  
  
> [!NOTE]
>  Dans la [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la bibliothèque parallèle de tâches et PLINQ fournissent des API pour le parallélisme des tâches et des données dans les programmes multithreads. Pour plus d’informations, consultez la page [Programmation parallèle](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Threads et threading](../../../docs/standard/threading/threads-and-threading.md)  
 Explique les avantages et les inconvénients de plusieurs threads et présente les scénarios dans lequel vous pouvez créer des threads ou utilisent des threads du pool.  
  
 [Exceptions dans les threads managés](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Décrit le comportement des exceptions non gérées dans les threads pour les différentes versions du .NET Framework, notamment les cas dans lesquels ils aboutit arrêt de l’application.  
  
 [Synchronisation des données pour le multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Décrit les stratégies de synchronisation des données dans les classes qui seront utilisées avec plusieurs threads.  
  
 [États des threads managés](../../../docs/standard/threading/managed-thread-states.md)  
 Décrit les États de thread de base et explique comment détecter si un thread est en cours d’exécution.  
  
 [Threads de premier plan et d'arrière-plan](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Explique les différences entre les threads de premier plan et d’arrière-plan.  
  
 [Threading managé et non managé dans Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Décrit la relation entre le threading managé et non managé, répertorie les équivalents managés de l’API de threading Windows et explique l’interaction des cloisonnements COM et les threads managés.  
  
 [Thread.Suspend, Garbage Collection et les points sans risque](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 Décrit le thread suspension et le garbage collection.  
  
 [Stockage local des threads : champs statiques et emplacements de données relatifs à un thread](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Décrit les mécanismes de stockage relatif aux threads.  
  
 [Annulation dans les threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 Décrit le fonctionnement asynchrones ou à long terme des opérations synchrones peut être annulé à l’aide d’un jeton d’annulation.  
  
## <a name="reference"></a>Référence  
 <xref:System.Threading.Thread>  
 Fournit la documentation de référence pour la classe **Thread** qui représente un thread managé, qu’elle provienne de code non managé ou qu’elle ait été créée dans une application managée.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Fournit un moyen sûr d’implémenter le multithreading conjointement avec les objets d’interface utilisateur.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Décrit les classes managées utilisées pour synchroniser les activités de plusieurs threads.  
  
 [Bonnes pratiques de threading géré](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Décrit les problèmes courants avec le multithreading et les stratégies pour éviter les problèmes.  
  
 [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)  
 Décrit la bibliothèque parallèle de tâches et PLINQ, qui simplifient considérablement le travail de création des applications .NET Framework asynchrones et multithreads.
