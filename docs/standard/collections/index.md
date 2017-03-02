---
title: "Collections et structures de données"
description: "Collections et structures de données"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9e70255a-c02a-4046-86b7-10c84bab2d38
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 30e53c38bd58e15668e01f2af79defb0a0918192
ms.lasthandoff: 03/02/2017

---

# <a name="collections-and-data-structures"></a>Collections et structures de données

Des données similaires peuvent souvent être gérées plus efficacement quand elles sont stockées et manipulées en tant que collection. Vous pouvez utiliser la classe [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array) ou les classes figurant dans les espaces de noms [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections), [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) ou [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) pour ajouter, supprimer et modifier des éléments individuels ou une plage d’éléments dans une collection.

Il existe deux principaux types de collections : les collections génériques et non génériques. Les collections génériques sont de type sécurisé au moment de la compilation. Pour cette raison, les collections génériques offrent généralement de meilleures performances. Les collections génériques acceptent un paramètre de type lorsqu’elles sont construites, et ne nécessitent pas de transtypage du type [Object](https://docs.microsoft.com/dotnet/core/api/System.Object) quand vous ajoutez ou supprimez des éléments de la collection. Les collections non génériques stockent des éléments comme [Object](https://docs.microsoft.com/dotnet/core/api/System.Object) et nécessitent un cast. Vous pouvez rencontrer des collections non génériques dans du code plus ancien.

Les collections figurant dans l’espace de noms [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) fournissent des opérations thread-safe efficaces pour accéder aux éléments de collection à partir de plusieurs threads.

## <a name="common-collection-features"></a>Fonctionnalités communes à toutes les collections

Toutes les collections fournissent des méthodes pour l'ajout, la suppression ou la recherche d'éléments au sein d'une collection. De plus, toutes les collections qui implémentent directement ou indirectement l’interface [ICollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection) ou [ICollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ICollection-1) partagent les fonctionnalités suivantes : 

* **Possibilité d'énumérer la collection**

   Les collections du .NET Framework implémentent [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) ou [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) pour permettre les itérations sur la collection. Un énumérateur peut être vu comme un pointeur mobile pointant vers n'importe quel élément d'une collection. L’instruction `foreach, in` (C#) utilise l’énumérateur exposé par la méthode `GetEnumerator` et masque la complexité de la manipulation de cet énumérateur. De plus, toute collection qui implémente [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) est considérée comme un type requêtable et peut être interrogée avec LINQ. Les requêtes LINQ fournissent un modèle commun d'accès aux données. Elles sont généralement plus concises et lisibles que les boucles for each standard, et fournissent des fonctionnalités de filtrage, de tri et de regroupement. Les requêtes LINQ peuvent également améliorer les performances.
    
* **La possibilité de copier le contenu d'une collection dans un tableau**

   Toutes les collections peuvent être copiées dans un tableau à l’aide de la méthode `CopyTo`. Toutefois, l’ordre des éléments dans le nouveau tableau s’appuie sur l’ordre dans lequel ils sont retournés par l’énumérateur. Le tableau résultant est toujours unidimensionnel avec une limite inférieure de zéro.
    
De plus, de nombreuses classes de collection comprennent les fonctionnalités suivantes :

* **Propriétés Capacity et Count**

   La propriété Capacity d'une collection indique le nombre d'éléments qu'elle peut contenir. La propriété Count d'une collection indique le nombre d'éléments qu'elle contient réellement. Certaines collections masquent l'une de ces propriétés, voire les deux.
    
   La capacité de la plupart des collections s'étend automatiquement quand la valeur de la propriété Capacity est atteinte. La mémoire est réallouée et les éléments sont copiés depuis l'ancienne collection vers la nouvelle. Cela permet de réduire le code nécessaire à l'utilisation de la collection. Toutefois, les performances de la collection peuvent être affectées. Par exemple, pour [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1), si `Count` est inférieur à `Capacity`, l’ajout d’un élément correspond à une opération O(1). Si la capacité doit être augmentée pour intégrer un nouvel élément, l'ajout d'un élément devient une opération O(n), où n est `Count`. Le meilleur moyen d'éviter la dégradation des performances en raison des réallocations est de définir la propriété Capacity sur la taille estimée de la collection. 
    
   [BitArray](https://docs.microsoft.com/dotnet/core/api/System.Collections.BitArray) est un cas particulier. Sa capacité est égale à sa longueur, qui est elle-même égale à son décompte.
    
*   **Une limite inférieure cohérente**

   La limite inférieure d'une collection est l'index de son premier élément. Toutes les collections indexées dans l’espace de noms [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) ont une limite inférieure de zéro, ce qui signifie qu’elles sont indexées à 0. Par défaut, [Array](https://docs.microsoft.com/dotnet/core/api/System.Array) possède une limite inférieure égale à zéro. Toutefois, une autre limite inférieure peut être définie quand vous créez une instance de la classe `Array` à l’aide de `Array.CreateInstance`.

*   **Synchronisation pour un accès depuis plusieurs threads** (classes [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) uniquement).

   Les types de collections non génériques de l’espace de noms [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) fournissent une certaine cohérence de thread pour la synchronisation, généralement exposée par les membres `SyncRoot` et `IsSynchronized`. Ces collections ne sont pas thread-safe par défaut. Si vous avez besoin d’un accès multithread évolutif et efficace pour une collection, utilisez l’une des classes de l’espace de noms [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) ou envisagez d’utiliser une collection immuable. Pour plus d’informations, consultez [Collections thread-safe](threadsafe/index.md).    
    
## <a name="choosing-a-collection"></a>Choix d'une collection 

En règle générale, vous devez utiliser des collections génériques. Le tableau suivant décrit certains scénarios courants concernant les collections, ainsi que les classes de collection que vous pouvez utiliser pour ces scénarios. Si vous ne connaissez pas encore les collections génériques, ce tableau vous aidera à choisir la collection générique qui répond le mieux à vos besoins.

Je souhaite : | Option(s) de collection générique | Option(s) de collection non générique
---------- | ---------------------------- | --------------------------------
Stocker les éléments sous forme de paires clé/valeur pour une recherche rapide par clé | [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) | [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable)
Accéder aux éléments par index | [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) | [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array), [System.Collections.ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList)
Utiliser des éléments premier entré, premier sorti (FIFO) | [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) | [System.Collections.Queue](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue)
Utiliser des données dernier entré, premier sorti (LIFO) | [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) | [System.Collections.Stack](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack)
Accéder aux éléments de manière séquentielle | [System.Collections.Generic.LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) | Aucune recommandation
Recevoir des notifications quand des éléments sont supprimés ou ajoutés à la collection. (implémente [INotifyPropertyChanged](https://docs.microsoft.com/dotnet/core/api/System.ComponentModel.INotifyPropertyChanged) et [INotifyCollectionChanged](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.INotifyCollectionChanged)) | [System.Collections.ObjectModel.ObservableCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.ObservableCollection-1) | Aucune recommandation
Utiliser une collection triée | [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) | [System.Collections.SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList)
Gérer l’accès et le stockage efficaces d’éléments uniques | [System.Collections.Generic.HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1), [System.Collections.Generic.SortedSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedSet-1) | Aucune recommandation

## <a name="related-topics"></a>Rubriques connexes

Titre | Description
----- | -----------
[Sélection d’une classe de collection](selecting-a-collection-class.md) | Décrit les différentes collections et permet d'en sélectionner une pour votre scénario.
[Types de collections couramment utilisés](commonly-used-collection-types.md) | Décrit les types de collections génériques et non génériques fréquemment utilisés, tels que [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array), [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) et [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2). 
[Quand utiliser les collections génériques](when-to-use-generic-collections.md) | Traite de l'utilisation des types de collections génériques.
[Comparaisons et tris dans les collections](comparisons-and-sorts-within-collections.md) | Aborde l'utilisation des comparaisons d'égalité et de tri dans les collections.
[Types de collections triées](sorted-collection-types.md) | Aborde les caractéristiques et les performances des collections triées.
[Types de collections Hashtable et Dictionary](hashtable-and-dictionary-collection-types.md) | Décrit les fonctionnalités des types de dictionnaires basés sur le hachage génériques et non génériques.
[Collections thread-safe](threadsafe/index.md) | Décrit les types de collections tels que [System.Collections.Concurrent.BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) et [System.Collections.Concurrent.ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) qui prennent en charge l’accès simultané sécurisé et efficace à partir de plusieurs threads.

## <a name="reference"></a>Référence

[System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array)

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized)

[System.Linq](https://docs.microsoft.com/dotnet/core/api/System.Linq)
  

