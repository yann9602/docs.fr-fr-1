---
title: Collections thread-safe
description: Collections thread-safe
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 92d5515d-f5d6-4a09-8bbb-31865d678643
translationtype: Human Translation
ms.sourcegitcommit: cfe65fcba1b3fdc09ffcac704a760d8ce29ea60b
ms.openlocfilehash: 421d46585b5d83f5772fa6596ad581c8c6acbf71

---

# <a name="threadsafe-collections"></a>Collections thread-safe

L’espace de noms [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) inclut plusieurs classes de collections qui sont à la fois thread-safe et évolutives. Plusieurs threads peuvent, sans risque et de façon efficace, ajouter ou supprimer des éléments dans ces collections, sans nécessiter une synchronisation supplémentaire dans le code utilisateur. Quand vous écrivez du nouveau code, utilisez les classes de collections simultanées chaque fois que la collection écrit simultanément dans plusieurs threads. Si vous effectuez uniquement une lecture à partir d’une collection partagée, vous pouvez utiliser les classes de l’espace de noms [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic). Nous vous recommandons de ne pas utiliser les classes de collections [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections), à moins que vous ne deviez cibler le runtime .NET Framework 1.1 ou une version antérieure.

## <a name="finegrained-locking-and-lockfree-mechanisms"></a>Verrouillage de granularité fine et mécanismes sans verrou

Certains types de collections simultanées utilisent des mécanismes de synchronisation légers tels que [SpinLock](https://docs.microsoft.com/dotnet/core/api/System.Threading.SpinLock), [SpinWait](https://docs.microsoft.com/dotnet/core/api/System.Threading.SpinWait), [SemaphoreSlim](https://docs.microsoft.com/dotnet/core/api/System.Threading.SemaphoreSlim) et [CountdownEvent](https://docs.microsoft.com/dotnet/core/api/System.Threading.CountdownEvent). Ces types de synchronisation utilisent généralement la rotation intensive pendant de courtes périodes avant de mettre le thread dans un véritable état d’attente.`Wait`. Lorsque les temps d’attente sont supposés être très courts, la rotation est beaucoup moins gourmande en ressources informatiques que l’attente, qui implique une transition de noyau coûteuse. Pour les classes de collections qui utilisent la rotation, cette efficacité signifie que plusieurs threads peuvent ajouter et supprimer des éléments à un taux très élevé.

Les classes [ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) et [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) n’utilisent pas du tout de verrous. Au lieu de cela, elles s’appuient sur des opérations Interlocked pour assurer la cohérence de thread.

> [!NOTE]
> Étant donné que les classes de collections simultanées prennent en charge [ICollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection), elles fournissent des implémentations pour les propriétés `IsSynchronized` et `SyncRoot`, bien que ces propriétés ne soient pas pertinentes. `IsSynchronized` retourne toujours `false` et `SyncRoot` a toujours la valeur Null.

Le tableau suivant répertorie les types de collections dans l’espace de noms [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent).

Type | Description
---- | -----------
[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) | Fournit des fonctionnalités de délimitation et de blocage pour tout type qui implémente [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1). Pour plus d’informations, consultez [Vue d’ensemble de BlockingCollection](blockingcollection-overview.md).
[ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) | Implémentation thread-safe d’une collection non ordonnée d’éléments.
[ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) | Implémentation thread-safe d’un dictionnaire de paires clé-valeur.
[ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) | Implémentation thread-safe d’une file d’attente FIFO (premier entré, premier sorti).
[ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) | Implémentation thread-safe d’une pile LIFO (dernier entré, premier sorti).
[IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) | Interface qu’un type doit implémenter pour être utilisé dans un `BlockingCollection`.

## <a name="thread-synchronization-in-the-net-framework-version-10-and-20-collections"></a>Synchronisation de threads dans les collections .NET Framework versions 1.0 et 2.0

Les collections introduites dans .NET Framework 1.0 se trouvent dans l’espace de noms [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections). Ces collections, qui incluent les [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) et [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) fréquemment utilisés, garantissent une sécurité des threads par le biais de la propriété `Synchronized`, qui retourne un wrapper thread-safe autour de la collection. Le wrapper fonctionne en verrouillant l’ensemble de la collection à chaque opération d’ajout ou de suppression. Par conséquent, chaque thread qui tente d’accéder à la collection doit attendre son tour pour prendre le verrou. Ce fonctionnement n’est pas évolutif et peut provoquer une importante dégradation des performances pour les grandes collections. De même, la conception n’est pas complètement protégée contre la concurrence critique. 

Les classes de collections introduites dans .NET Framework 2.0 se trouvent dans l’espace de noms [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic). Il s’agit notamment de [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1), [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2), etc. Ces classes garantissent une cohérence des types et des performances améliorées par rapport aux classes `System.Collections`. Toutefois, les classes de collections `System.Collections.Generic` ne fournissent pas de synchronisation des threads. Le code utilisateur doit fournir toute la synchronisation quand des éléments sont ajoutés ou supprimés simultanément sur plusieurs threads.

Nous vous recommandons les classes de collections `System.Collections.Concurrent`, car elles offrent non seulement la cohérence des types des classes de collections `System.Collections.Generic`, mais également une cohérence de thread plus efficace et plus complète que les collections `System.Collections`.

## <a name="related-topics"></a>Rubriques connexes

Titre | Description
----- | -----------
[Vue d'ensemble de BlockingCollection](blockingcollection-overview.md) | Décrit la fonctionnalité fournie par le type `BlockingCollection<T>`.
[Quand utiliser une collection thread-safe](when-to-use-a-thread-safe-collection.md) | Explique quand il est approprié d’utiliser une collection thread-safe.
[Guide pratique pour ajouter et supprimer des éléments d'un ConcurrentDictionary](how-to-add-and-remove-items.md) | Décrit comment ajouter et supprimer des éléments dans un `ConcurrentDictionary<TKey, TValue>`.
[Guide pratique pour ajouter et prendre des éléments individuellement dans un BlockingCollection](how-to-add-and-take-items.md) | Décrit comment ajouter et récupérer des éléments dans une collection de blocage sans utiliser l’énumérateur en lecture seule.
[Guide pratique pour ajouter des fonctionnalités de délimitation et de blocage à une collection](how-to-add-bounding-and-blocking.md ) | Décrit comment utiliser une classe de collection comme mécanisme de stockage sous-jacent pour une collection `IProducerConsumerCollection<T>;`.
[Guide pratique pour utiliser la boucle ForEach pour supprimer les éléments d'un BlockingCollection](how-to-use-foreach-to-remove.md ) | Décrit comment utiliser `foreach` pour supprimer tous les éléments d’une collection de blocage.
[Guide pratique pour utiliser des tableaux de collections de blocage dans un pipeline](how-to-use-arrays-of-blockingcollections.md) | Décrit comment utiliser simultanément plusieurs collections de blocage pour implémenter un pipeline.
[Guide pratique pour créer un pool d'objets à l'aide d'un ConcurrentBag](how-to-create-an-object-pool.md) | Montre comment utiliser un conteneur simultané pour améliorer les performances dans les scénarios où vous pouvez réutiliser des objets au lieu d’en créer continuellement de nouveaux.

## <a name="reference"></a>Référence

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)






 





<!--HONumber=Nov16_HO1-->


