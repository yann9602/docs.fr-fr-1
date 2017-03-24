---
title: "Quand utiliser les collections génériques"
description: "Quand utiliser les collections génériques"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 971e08bd-b63f-4832-9e61-9f65cbedd352
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: bde317c165981775330e1d0d8261d355e2401bc9
ms.lasthandoff: 03/13/2017

---

# <a name="when-to-use-generic-collections"></a>Quand utiliser les collections génériques

L'utilisation de collections génériques est généralement recommandée, car elle permet de bénéficier immédiatement de la cohérence des types sans avoir à dériver d'un type de collection de base et à implémenter des membres spécifiques au type. Les types de collections génériques sont généralement plus performants que leurs équivalents non génériques (et mieux que les types dérivés de types de collections de base non génériques) quand les éléments de collection sont des types valeur, car grâce aux génériques, aucun boxing d’éléments n’est nécessaire. 

Vous devez utiliser les classes de collection génériques dans l’espace de noms [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) quand plusieurs threads sont susceptibles d’ajouter ou de supprimer simultanément des éléments de la collection.

Les types génériques suivants correspondent à des types de collections existants : 

*   [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) est la classe générique qui correspond à [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList).

*   [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) et [ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) sont les classes génériques qui correspondent à [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable). 

*   [Collection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.Collection-1) est la classe générique qui correspond à [CollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.CollectionBase). `Collection<T>` peut être utilisée comme classe de base, mais contrairement à `CollectionBase`, elle n'est pas abstraite. Cela la rend plus facile à utiliser.

*   [ReadOnlyCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.ReadOnlyCollection-1) est la classe générique qui correspond à [ReadOnlyCollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.ReadOnlyCollectionBase). `ReadOnlyCollection<T>` n’est pas abstraite et dispose d’un constructeur qui facilite l’exposition d’une [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) existante sous la forme d’une collection en lecture seule.

*   Les classes génériques [Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1), [ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1), [Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1), [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) et [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) correspondent aux classes non génériques respectives du même nom.

## <a name="additional-types"></a>Autres types

Plusieurs types de collections génériques n'ont pas d'équivalents non génériques. Il s'agit notamment des types suivants : 

*   [LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) est une liste liée à usage général qui fournit des opérations d’insertion et de suppression O(1).

*   [SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) est un dictionnaire trié avec des opérations d’insertion et d’extraction O(log n), ce qui en fait une alternative pratique à [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2). 

*   [KeyedCollection&lt;TKey, TItem&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) est un hybride entre une liste et un dictionnaire qui permet de stocker des objets qui contiennent leurs propres clés.

*   [BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) implémente une classe de collection avec des fonctionnalités de délimitation et de blocage.

*   [ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) permet une insertion et une suppression rapides des éléments non triés.

## <a name="linq-to-objects"></a>LINQ to Objects

La fonctionnalité LINQ to Objects vous permet d’utiliser des requêtes LINQ pour accéder aux objets en mémoire pour autant que le type d’objet implémente l’interface [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) ou [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1). Les requêtes LINQ fournissent un modèle commun pour accéder aux données, sont généralement plus concises et lisibles que les boucles `foreach` standard et intègrent des fonctions de filtrage, de classement et de regroupement. Les requêtes LINQ peuvent également améliorer les performances.

## <a name="additional-functionality"></a>Autres fonctionnalités

Certains types génériques ont des fonctionnalités que n’ont pas les types de collections non génériques. Par exemple, la classe [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1), qui correspond à la classe non générique [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList), possède plusieurs méthodes acceptant des délégués génériques, tels que le délégué [Predicate&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Predicate-1), qui permet de spécifier des méthodes pour effectuer des recherches dans la liste, et le délégué [Action&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Action-1), qui représente des méthodes qui agissent sur chaque élément de la liste.

La classe [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) vous permet de spécifier vos propres implémentations d’interface générique [IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) pour trier et parcourir la liste. Les classes [SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) et [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) possèdent également cette fonctionnalité. De plus, ces classes permettent de spécifier des comparateurs au moment de la création de la collection. De la même façon, les classes [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) et [KeyedCollection&lt;TKey, TItem&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) vous permettent de spécifier vos propres comparateurs d’égalité.

## <a name="see-also"></a>Voir aussi

[Collections et structures de données](index.md) 

[Types de collection couramment utilisés](commonly-used-collection-types.md)

