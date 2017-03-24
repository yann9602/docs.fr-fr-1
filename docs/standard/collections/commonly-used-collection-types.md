---
title: "Types de collections couramment utilisés"
description: "Types de collections couramment utilisés"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 55861611-1e40-4cc2-9ec5-0b2df4ba6c0c
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: f44b8a87bf263032b991fc1bbc70712136910106
ms.lasthandoff: 03/13/2017

---

# <a name="commonly-used-collection-types"></a>Types de collections couramment utilisés

Les types de collections sont des variations courantes des collections de données, telles que les tables de hachage, les files d’attente, les piles, les conteneurs, les dictionnaires et les listes.

Les collections sont basées sur l’interface [`ICollection`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection), [`IList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList) ou [`IDictionary`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary), ou sur leurs équivalents génériques. Les interfaces `IList` et `IDictionary` sont toutes deux dérivées de l'interface `ICollection`. Par conséquent, toutes les collections sont basées directement ou indirectement sur l'interface `ICollection`. Dans les collections basées sur l’interface `IList` (telles que [`Array`](https://docs.microsoft.com/dotnet/core/api/System.Array), [`ArrayList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) ou [`List<T>)`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1)) ou directement sur l’interface `ICollection` (telles que [`Queue`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue), [`ConcurrentQueue<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1), [`Stack`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack), [`ConcurrentStack<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) ou [`LinkedList<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1)), chaque élément contient uniquement une valeur. Dans les collections basées sur l’interface `IDictionary` (telles que les classes [`Hashtable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) et [`SortedList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList), les classes génériques [`Dictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) et [`SortedList<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2)) ou sur les classes [`ConcurrentDictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2), chaque élément contient à la fois une clé et une valeur. La classe [`KeyedCollection<TKey, TItem>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) est unique, car il s’agit d’une liste de valeurs auxquelles sont incorporées des clés. Son comportement est donc celui d’une liste ou d’un dictionnaire.

Les collections génériques conviennent le mieux au typage fort. Toutefois, si votre langage ne prend pas en charge les génériques, l’espace de noms [`System.Collections`](https://docs.microsoft.com/dotnet/core/api/System.Collections) contient des collections de base, telles que [`CollectionBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.CollectionBase), [`ReadOnlyCollectionBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ReadOnlyCollectionBase) et [`DictionaryBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.DictionaryBase), qui sont des classes de base abstraites pouvant être étendues pour créer des classes de collection fortement typées. Quand un accès efficace à une collection multithread est requis, utilisez les collections génériques de l’espace de noms [`System.Collections.Concurrent`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent).

Les collections peuvent varier, en fonction de la façon dont les éléments sont stockés et triés, ainsi que de la façon dont les recherches et les comparaisons sont effectuées. La classe [`Queue`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue) et la classe générique [`Queue<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) fournissent des listes premier entré, premier sorti (FIFO), alors que la classe [`Stack`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack) et la classe générique [`Stack<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) fournissent des listes dernier entré, premier sorti (LIFO). La classe [`SortedList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) et la classe générique [`SortedList<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) fournissent des versions triées de la classe [`Hashtable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) et de la classe générique [`Dictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2). Les éléments d’un `Hashtable` ou d’un `Dictionary<TKey, TValue>` sont accessibles uniquement via la clé de l’élément, alors que les éléments d’un `SortedList` ou d’un [`KeyedCollection<TKey, TItem>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) sont accessibles aussi bien via la clé que via l’index de l’élément. Les index de toutes les collections sont de base zéro, à l’exception de [`Array`](https://docs.microsoft.com/dotnet/core/api/System.Array), qui acceptent les tableaux qui ne sont pas de base zéro.

La fonctionnalité LINQ to Objects permet d’utiliser des requêtes LINQ pour accéder aux objets en mémoire tant que le type d’objet implémente l’interface [`IEnumerable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) ou [`IEnumerable<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1). Les requêtes LINQ fournissent un modèle commun pour accéder aux données, sont généralement plus concises et lisibles que les boucles foreach standard et intègrent des fonctions de filtrage, de classement et de regroupement. Les requêtes LINQ peuvent également améliorer les performances.

## <a name="related-topics"></a>Rubriques connexes

Titre | Description
----- | -----------
[`Collections and Data Structures`](index.md) | Présente les différents types de collection disponibles dans le .NET Framework, notamment les piles, les files d’attente, les listes, les tableaux et les dictionnaires.
[`Hashtable and Dictionary Collection Types`](hashtable-and-dictionary-collection-types.md) | Décrit les fonctionnalités des types de dictionnaires basés sur le hachage génériques et non génériques.
[`Sorted Collection Types`](sorted-collection-types.md) | Décrit les caractéristiques et les performances des collections triées.

## <a name="reference"></a>Référence

[`System.Collections`](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[`System.Collections.Generic`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[`System.Collections.ICollection`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection)

[`System.Collections.Generic.ICollection<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ICollection-1)

[`System.Collections.IList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList)

[`System.Collections.Generic.IList<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1)

[`System.Collections.IDictionary`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)

[`System.Collections.Generic.IDictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)

[`System.Linq`](https://docs.microsoft.com/dotnet/core/api/System.Linq)

