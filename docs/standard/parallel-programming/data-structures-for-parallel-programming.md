---
title: "Structures de données pour la programmation parallèle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f35c5382455021f0a001604367e59204ce4ad93c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="data-structures-for-parallel-programming"></a>Structures de données pour la programmation parallèle
Le .NET Framework version 4 introduit plusieurs nouveaux types qui sont utiles dans la programmation parallèle, y compris un ensemble de classes de collection simultanée, les primitives de synchronisation légers et les types pour l’initialisation tardive. Vous pouvez utiliser ces types avec n’importe quel code d’application multithread, y compris la bibliothèque parallèle de tâches et PLINQ.  
  
## <a name="concurrent-collection-classes"></a>Classes de Collection simultanée  
 Classes de la collection dans le <xref:System.Collections.Concurrent?displayProperty=nameWithType> espace de noms fournissent thread-safe ajouter et supprimer les opérations qui éviter autant que possible les verrous et utiliser le verrouillage de granularité fine là où les verrous sont nécessaires. Contrairement aux regroupements qui ont été introduites dans les versions 1.0 et 2.0 du .NET Framework, une classe de collection simultanée ne nécessite pas de code utilisateur acquière des verrous lorsqu’il accède à des éléments. Les classes de collection simultanée peuvent améliorer considérablement les performances des types tels que <xref:System.Collections.ArrayList?displayProperty=nameWithType> et <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (avec le verrouillage implémenté par l’utilisateur) dans les scénarios où plusieurs threads ajoutent et suppriment des éléments d’une collection.  
  
 Le tableau suivant répertorie les nouvelles classes de collection simultanée :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Fournit des fonctions bloquantes et englobantes pour les collections thread-safe qui implémentent <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Threads producteurs se bloquent si aucun emplacement n’est disponible ou si la collection est complète. Threads de consommateur se bloquer si la collection est vide. Ce type prend également en charge les accès non bloquant par les producteurs et consommateurs. <xref:System.Collections.Concurrent.BlockingCollection%601>peut être utilisé comme classe de base ou magasin de stockage pour fournir bloquantes et englobantes pour les classes de collection qui prend en charge <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Une implémentation de conteneur thread-safe qui fournit évolutive ajouter et obtenir des opérations.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Un type de dictionnaire simultané et évolutif.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Une file d’attente de FIFO simultanée et évolutive.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Pile LIFO simultanée et évolutive.|  
  
 Pour plus d’informations, consultez [Collections thread-safe](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Primitives de synchronisation  
 Les nouvelles primitives de synchronisation dans le <xref:System.Threading?displayProperty=nameWithType> espace de noms permettent affinée simultanéité et améliorer les performances en évitant les mécanismes de verrouillage coûteux trouvés dans le code multithread hérité. Certains des nouveaux types, tels que <xref:System.Threading.Barrier?displayProperty=nameWithType> et <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> ont pas d’équivalents dans les versions antérieures du .NET Framework.  
  
 Le tableau suivant répertorie les nouveaux types de synchronisation :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Permet à plusieurs threads fonctionner en parallèle sur un algorithme en fournissant un point auquel chaque tâche peut signaler son arrivée et bloquer ensuite jusqu'à ce que certaines ou toutes les tâches sont arrivés. Pour plus d’informations, voir [Cloisonnement](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Simplifie les scénarios de bifurcation et de jointure en fournissant un mécanisme de rendez-vous facile. Pour plus d’informations, consultez [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Une primitive de synchronisation similaire à <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim>est léger mais peut être utilisé uniquement pour la communication intra-PROCEDE. Pour plus d’informations, consultez [ManualResetEvent et ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md).|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Primitive de synchronisation qui limite le nombre de threads qui peuvent accéder simultanément à une ressource ou un pool de ressources. Pour plus d’informations, consultez [Semaphore et SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Une primitive de verrou d’exclusion mutuelle qui oblige le thread qui essaie d’acquérir le verrou peut attendre dans une boucle, ou *spin*, pour une période de temps avant de transmettre son quantum. Dans les scénarios où l’attente du verrou est censée être courte, <xref:System.Threading.SpinLock> offre de meilleures performances que les autres types de verrouillage. Pour plus d’informations, consultez [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Un type petit et léger qui sera tourner pendant une période donnée et éventuellement mettre le thread dans un état d’attente si le nombre de sélection numérique est dépassé.  Pour plus d’informations, consultez [SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Pour plus d'informations, voir :  
  
-   [Guide pratique pour utiliser le verrouillage SpinLock pour une synchronisation de bas niveau](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [Comment : synchroniser des opérations simultanées avec un objet Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Classes d’initialisation tardive  
 Avec l’initialisation tardive, la mémoire pour un objet n’est pas allouée jusqu'à ce qu’il est nécessaire. L’initialisation tardive peut améliorer les performances en répartissant les allocations d’objets uniformément sur la durée de vie d’un programme. Vous pouvez activer l’initialisation tardive pour tout type personnalisé en encapsulant le type <xref:System.Lazy%601>.  
  
 Le tableau suivant répertorie les types de l’initialisation tardive :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Fournit un léger, thread-safe à l’initialisation tardive.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Fournit une valeur initialisée tardivement sur une base par thread, avec chaque thread appelant de façon tardive la fonction d’initialisation.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Fournit des méthodes statiques qui vous éviter d’avoir à allouer une instance dédiée de l’initialisation tardive. Au lieu de cela, ils permet de références pour vérifier cibles ont été initialisées lors de leur accès.|  
  
 Pour plus d’informations, consultez [Initialisation tardive](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Agréger des Exceptions  
 Le <xref:System.AggregateException?displayProperty=nameWithType> type peut être utilisé pour capturer plusieurs exceptions qui sont levées simultanément sur des threads séparés et les retournent au thread joint comme une exception. Le <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> types et PLINQ utilisent <xref:System.AggregateException> largement à cet effet. Pour plus d’informations, consultez [NIB : Comment : Handle Exceptions Thrown by Tasks](http://msdn.microsoft.com/en-us/d6c47ec8-9de9-4880-beb3-ff19ae51565d) et [Comment : gérer des Exceptions dans une requête PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Threading?displayProperty=nameWithType>  
 [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)
