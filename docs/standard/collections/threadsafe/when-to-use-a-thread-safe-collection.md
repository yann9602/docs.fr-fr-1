---
title: Quand utiliser une collection thread-safe
description: Quand utiliser une collection thread-safe
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a2a42d44-f6a5-4f16-9000-026221d66349
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: b0b88a85cb4048849464381656a30e8c8ea694d8
ms.lasthandoff: 03/13/2017

---

# <a name="when-to-use-a-thread-safe-collection"></a>Quand utiliser une collection thread-safe

Les types de collection `ConcurrentQueue`, `ConcurrentStack`, `ConcurrentDictionary`, `ConcurrentBag` et `BlockingCollection` sont spécialement conçus pour prendre en charge les opérations d’ajout et de suppression multithread. Pour garantir la cohérence de thread, ces nouveaux types utilisent différentes sortes de mécanismes de verrouillage et de synchronisation sans verrou efficaces. La synchronisation ajoute une surcharge à une opération. La quantité de la surcharge dépend du genre de synchronisation utilisé, du genre d’opérations exécutées et d’autres facteurs tels que le nombre de threads qui tentent d’accéder simultanément à la collection.

Dans certains scénarios, la surcharge de synchronisation est négligeable et permet au type multithread de s’exécuter beaucoup plus rapidement et d’évoluer beaucoup mieux que son équivalent qui n’est pas thread-safe quand il est protégé par un verrou externe. Dans d’autres scénarios, la surcharge peut entraîner une exécution et une scalabilité du type thread-safe à peu près identiques, ou même plus lentes, que celles de la version du type qui n’est pas thread-safe et qui est verrouillée de manière externe.

Les sections suivantes fournissent des recommandations générales concernant le moment où utiliser une collection thread-safe ou son équivalent non thread-safe qui a un verrou fourni par l’utilisateur autour de ses opérations de lecture et d’écriture. Étant donné que les performances peuvent varier en fonction de nombreux facteurs, ces recommandations ne sont pas spécifiques et ne sont pas nécessairement valables dans toutes les circonstances. Si les performances sont très importantes, la meilleure façon de déterminer le type de collection à utiliser consiste à mesurer les performances en fonction de configurations et de charges d’ordinateur représentatives. Ce document utilise les termes suivants :

*Scénario producteur-consommateur pur :* Tout thread donné ajoute ou supprime des éléments, mais pas les deux.

*Scénario producteur-consommateur mixte :* Tout thread donné ajoute et supprime des éléments.

*Accélération :* Performances algorithmiques plus rapides par rapport à un autre type dans le même scénario.

*Scalabilité :* Augmentation des performances proportionnelle au nombre de cœurs de l’ordinateur. Un algorithme évolutif s’exécute plus vite sur huit cœurs que sur deux cœurs.

## <a name="concurrentqueuelttgt-vs-queuelttgt"></a>Comparaison de ConcurrentQueue&lt;T&gt; et de Queue&lt;T&gt;

Dans les scénarios producteur-consommateur purs, où le temps de traitement de chaque élément est très court (quelques instructions), [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) peut offrir des avantages modestes en matière de performances par rapport à un [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) qui a un verrou externe. Dans ce scénario, `ConcurrentQueue<T>` fonctionne mieux quand un thread dédié effectue la mise en file d’attente et qu’un autre thread dédié annule la mise en file d’attente. Si vous n’appliquez pas cette règle, `Queue<T>` peut même s’exécuter légèrement plus rapidement que `ConcurrentQueue<T>` sur les ordinateurs à plusieurs cœurs. 

Quand le temps de traitement est autour de 500 opérations en virgule flottante (FLOPS), ou plus, la règle de deux threads ne s’applique pas à `ConcurrentQueue<T>`, qui possède alors une très bonne scalabilité. `Queue<T>` n’évolue pas bien dans ce scénario.

Dans les scénarios producteur-consommateur mixtes, quand le temps de traitement est très court, un `Queue<T>` qui a un externe verrou évolue mieux que `ConcurrentQueue<T>`. Toutefois, quand le temps de traitement est autour de 500 opérations en virgule flottante (FLOPS), ou plus, `ConcurrentQueue<T>` évolue mieux.

## <a name="concurrentstack-vs-stack"></a>Comparaison de ConcurrentStack et de Stack

Dans les scénarios producteur-consommateur purs, quand le temps de traitement est très court, [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) et [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) qui a un verrou externe s’exécuteront probablement de la même manière avec un thread d’exécution de type push dédié et un thread d’exécution de type pop dédié. Toutefois, à mesure que le nombre de threads augmente, les deux types ralentissent à cause de l’augmentation des conflits, et `Stack<T>` peut fonctionner mieux que `ConcurrentStack<T>`. Quand le temps de traitement est autour de 500 opérations en virgule flottante (FLOPS), ou plus, les deux types évoluent à peu près au même rythme. 

Dans les scénarios producteur-consommateur mixtes, `ConcurrentStack<T>` est plus rapide à la fois pour les petites et les grandes charges de travail.

L’utilisation de `PushRange` et de `TryPopRange` peut accélérer considérablement les temps d’accès.

## <a name="concurrentdictionary-vs-dictionary"></a>Comparaison de ConcurrentDictionary et de Dictionary

En général, utilisez un [System.Collections.Concurrent.ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) dans tout scénario où vous ajoutez et mettez à jour des clés ou des valeurs simultanément à partir de plusieurs threads. Dans les scénarios qui impliquent des mises à jour fréquentes et des lectures relativement peu nombreuses, `ConcurrentDictionary<TKey, TValue>` offre généralement des avantages modestes. Dans les scénarios qui impliquent de nombreuses lectures et de nombreuses mises à jour, `ConcurrentDictionary<TKey, TValue>` est généralement beaucoup plus rapide, quel que soit le nombre de cœurs des ordinateurs.

Dans les scénarios qui impliquent des mises à jour fréquentes, vous pouvez augmenter le degré d’accès concurrentiel dans `ConcurrentDictionary<TKey, TValue>`, puis mesurer pour voir si les performances augmentent sur les ordinateurs qui ont plus de cœurs. Si vous modifiez le niveau d’accès concurrentiel, évitez, autant que possible, les opérations globales.

Si vous lisez uniquement une clé ou des valeurs, [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) est plus rapide car aucune synchronisation n’est nécessaire si le dictionnaire n’est pas modifié par des threads.

## <a name="concurrentbag"></a>ConcurrentBag

Dans les scénarios producteur-consommateur purs, [System.Collections.Concurrent.ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) s’exécutera probablement plus lentement que les autres types de collections simultanées.

Dans les scénarios producteur-consommateur mixtes, `ConcurrentBag<T>` est généralement beaucoup plus rapide et plus évolutif que les autres types de collections simultanées à la fois pour les petites et pour les grandes charges de travail.

## <a name="blockingcollection"></a>BlockingCollection

Quand une sémantique de délimitation et de blocage est nécessaire, [System.Collections.Concurrent.BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) s’exécutera probablement plus rapidement que toute implémentation personnalisée. Il prend également en charge une gestion enrichie des annulations, énumérations et exceptions.

## <a name="see-also"></a>Voir aussi

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[Collections thread-safe](index.md)

