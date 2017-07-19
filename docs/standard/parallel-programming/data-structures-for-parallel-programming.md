---
title: "Data Structures for Parallel Programming | Microsoft Docs"
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
  - "data structures, multi-threading"
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Data Structures for Parallel Programming
Le .NET Framework version 4 contient plusieurs nouveaux types utiles pour la programmation parallèle, notamment un ensemble de classes de collection simultanée, des primitives de synchronisation légères et des types pour l'initialisation tardive.  Vous pouvez utiliser ces types avec tout code d'application multithread, notamment avec la bibliothèque parallèle de tâches et PLINQ.  
  
## Classes de collection simultanée  
 Les classes de collection de l'espace de noms <xref:System.Collections.Concurrent?displayProperty=fullName> permettent des opérations d'ajout et de suppression thread\-safe qui évitent les verrous lorsque cela est possible et utilisent un verrouillage affiné lorsque l'utilisation de verrous est nécessaire.  Contrairement aux collections présentées dans le .NET Framework version 1.0 et 2.0, une classe de collection simultanée ne nécessite pas que le code utilisateur acquière des verrous lorsqu'il accède à des éléments.  Les classes de collection simultanée peuvent améliorer considérablement les performances des types tels que <xref:System.Collections.ArrayList?displayProperty=fullName> et <xref:System.Collections.Generic.List%601?displayProperty=fullName> \(avec verrouillage implémenté par utilisateur\) dans les scénarios où plusieurs threads ajoutent et suppriment des éléments d'une collection.  
  
 Le tableau suivant répertorie les nouvelles classes de collection simultanée :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName>|Fournit des fonctions bloquantes et englobantes pour les collections thread\-safe qui implémentent <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName>.  Les threads producteurs se bloquent si aucun emplacement n'est disponible ou si la collection est complète.  Les threads consommateurs se bloquent si la collection est vide.  Ce type prend également en charge l'accès non bloquant par les consommateurs et les producteurs.  <xref:System.Collections.Concurrent.BlockingCollection%601> peut être utilisé comme classe de base ou magasin de stockage pour le blocage et la délimitation des classes de collection prenant en charge <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName>|Une implémentation de sac thread\-safe qui permet des opérations évolutives d'ajout et d'extraction.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>|Type de dictionnaire simultané et évolutif.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>|File d'attente FIFO simultanée et évolutive.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName>|Pile LIFO simultanée et évolutive.|  
  
 Pour plus d'informations, consultez [Collections thread\-safe](../../../docs/standard/collections/thread-safe/index.md).  
  
## Primitives de synchronisation  
 Les nouvelles primitives de synchronisation dans l'espace de noms <xref:System.Threading?displayProperty=fullName> permettent l'accès concurrentiel à grains fins et de meilleures performances en évitant les mécanismes de verrouillage coûteux trouvés dans le code multithread hérité.  Certains nouveaux types, tels que <xref:System.Threading.Barrier?displayProperty=fullName> et <xref:System.Threading.CountdownEvent?displayProperty=fullName> n'ont pas d'équivalents dans les premières version du .NET Framework.  
  
 Le tableau suivant répertorie les nouveaux types de synchronisation :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=fullName>|Permet à plusieurs threads de travailler en parallèle sur un algorithme en fournissant un point auquel chaque tâche peut signaler son arrivée puis se bloquer jusqu'à ce que certaines ou toutes les tâches soient arrivées.  Pour plus d'informations, consultez [Barrier](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=fullName>|Simplifie les scénarios de bifurcation\/jointure en fournissant un mécanisme de rendez\-vous facile.  Pour plus d'informations, consultez [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=fullName>|Synchronisation de base semblable à <xref:System.Threading.ManualResetEvent?displayProperty=fullName>.  <xref:System.Threading.ManualResetEventSlim> est léger mais peut être utilisé uniquement pour la communication intra\-processus.  Pour plus d'informations, consultez [ManualResetEvent and ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md).|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=fullName>|Primitive de synchronisation qui limite le nombre de threads qui peuvent accéder simultanément à une ressource ou un pool de ressources.  Pour plus d'informations, consultez [Semaphore and SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=fullName>|Primitive de verrou d'exclusion mutuelle qui fait attendre dans une boucle \(ou *tourner*\) le thread qui essaie d'acquérir le verrou pendant une certaine durée avant de transmettre son quantum.  Dans les scénarios où l'attente du verrou est censée être courte, <xref:System.Threading.SpinLock> offre de meilleures performances que les autres types de verrouillage.  Pour plus d'informations, consultez [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=fullName>|Type petit et léger qui tournera pendant une durée spécifiée et mettra finalement le thread en état d'attente si le nombre de tours est dépassé.  Pour plus d'informations, consultez [SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Pour plus d'informations, consultez :  
  
-   [How to: Use SpinLock for Low\-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## Classes d'initialisation tardive  
 Avec l'initialisation tardive, la mémoire d'un objet n'est pas allouée tant que cela n'est pas nécessaire.  L'initialisation tardive peut améliorer les performances en répartissant de façon égale les allocations d'objets pendant la durée de vie d'un programme.  Vous pouvez activer l'initialisation tardive pour tout type personnalisé en incluant dans un wrapper le type <xref:System.Lazy%601>.  
  
 Le tableau suivant répertorie les types d'initialisation tardive :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=fullName>|Fournit une initialisation tardive légère et thread\-safe.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=fullName>|Fournit une valeur initialisée de façon tardive par thread, avec chaque thread appelant de façon tardive la fonction d'initialisation.|  
|<xref:System.Threading.LazyInitializer?displayProperty=fullName>|Fournit des méthodes statiques qui évitent le besoin d'allouer une instance d'initialisation tardive dédiée.  À la place, elles utilisent des références pour vérifier que les cibles ont été initialisées.|  
  
 Pour plus d'informations, consultez [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).  
  
## Agrégat d'exceptions  
 Le type <xref:System.AggregateException?displayProperty=fullName> peut être utilisé pour capturer plusieurs exceptions levées simultanément sur des threads séparés et les retourner au thread joint comme une exception unique.  Les types <xref:System.Threading.Tasks.Task?displayProperty=fullName> et <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> et PLINQ utilisent largement <xref:System.AggregateException> à cette fin.  Pour plus d’informations, consultez [NIB: How to: Handle Exceptions Thrown by Tasks](http://msdn.microsoft.com/fr-fr/d6c47ec8-9de9-4880-beb3-ff19ae51565d) et [How to: Handle Exceptions in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## Voir aussi  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 <xref:System.Threading?displayProperty=fullName>   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)