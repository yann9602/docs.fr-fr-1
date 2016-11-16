---
title: "Sélection d’une classe de collection"
description: "Sélection d’une classe de collection"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 0a60fca7-e082-48d4-9dda-30b0d3e67ec7
translationtype: Human Translation
ms.sourcegitcommit: cfe65fcba1b3fdc09ffcac704a760d8ce29ea60b
ms.openlocfilehash: f00fedb70bddc184e5c6ea71213b2beb78594792

---

# <a name="selecting-a-collection-class"></a>Sélection d’une classe de collection

Veillez à choisir votre classe de collection avec soin. L’utilisation d’un type incorrect peut limiter votre utilisation de la collection. Les versions génériques et simultanées des collections doivent être préférées en raison de leur sécurité supérieure des types et d'autres améliorations. En règle générale, évitez d’utiliser les types de l’espace de noms System.Collections, sauf si vous ciblez spécifiquement le .NET Framework version 1.1. 

Considérez les questions suivantes :

* Avez-vous besoin d'une liste séquentielle où l'élément est en général abandonné une fois sa valeur récupérée ? 

    * Si oui, envisagez d’utiliser la classe générique [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) si vous avez besoin d’un comportement premier entré, premier sorti (FIFO, First-In, First-Out). Envisagez d’utiliser la classe générique [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) si vous avez besoin d’un comportement dernier entré, premier sorti (LIFO, Last-In, First-Out). Pour un accès sécurisé à partir de plusieurs threads, utilisez les versions simultanées [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) et [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1).
    
    * Si ce n'est pas le cas, envisagez d'utiliser les autres collections.
    
* Avez-vous besoin d'accéder aux éléments dans un certain ordre, comme FIFO ou LIFO, ou de façon aléatoire ?

    * La classe générique [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) ou [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) propose un accès FIFO. Pour plus d’informations, consultez [Quand utiliser une collection thread-safe](threadsafe/when-to-use-a-thread-safe-collection.md).
    
    * La classe générique [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) ou [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) propose un accès LIFO. Pour plus d’informations, consultez [Quand utiliser une collection thread-safe](threadsafe/when-to-use-a-thread-safe-collection.md).
    
    * La classe générique [System.Collections.Generic.LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) autorise un accès séquentiel de haut en bas ou de bas en haut.
    
* Avez-vous besoin d'accéder à chaque élément selon son index ? 

    * La classe [System.Collections.Specialized.StringCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringCollection) et la classe générique [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) offrent un accès à leurs éléments via l’index de base zéro de l’élément. 
    
    * Les classes [System.Collections.Specialized.ListDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.ListDictionary) et [System.Collections.Specialized.StringDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringDictionary), et les classes génériques [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) et [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) offrent l’accès à leurs éléments via la clé de l’élément.
    
    * Les classes [System.Collections.Specialized.NameObjectCollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameObjectCollectionBase) et [System.Collections.Specialized.NameValueCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameValueCollection), et les classes génériques [System.Collections.ObjectModel.KeyedCollection&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) et [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) offrent l’accès à leurs éléments via l’index de base zéro ou la clé de l’élément.
    
* Chaque élément contiendra-t-il une valeur, une combinaison d'une clé et d'une valeur, ou une combinaison d'une clé et de plusieurs valeurs ? 

    * Une valeur : Utilisez l’une quelconque des collections basées sur l’interface générique [System.Collections.Generic.IList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1).
    
    * Une clé et une valeur : Utilisez l’une quelconque des collections basées sur l’interface générique [System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2).
    
    * Une valeur avec une clé incorporée : Utilisez la classe générique [System.Collections.ObjectModel.KeyedCollection&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2).
    
    * Une clé et plusieurs valeurs : Utilisez la classe [System.Collections.Specialized.NameValueCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameValueCollection).
    
* Avez-vous besoin de trier les éléments différemment de la façon dont ils ont été entrés ? 

    * La classe [System.Collections.Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) trie ses éléments par leurs codes de hachage.
    
    * Les classes génériques [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) et [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) trient leurs éléments par la clé, selon les implémentations de l’interface [System.Collections.IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer) et de l’interface générique [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1).
    
    * La classe générique [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) fournit une méthode `Sort` qui prend une implémentation de l’interface générique `IComparer<T>` comme paramètre.
    
* Avez-vous besoin de collections qui acceptent seulement des chaînes ? 

    * [StringCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringCollection) (basé sur [System.Collections.IList](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList)) et [StringDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringDictionary) (basé sur [System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)) se trouvent dans l’espace de noms [System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized). 
    
    * En outre, vous pouvez utiliser toutes les classes de collection génériques dans l’espace de noms [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) comme des collections de chaînes fortement typées en spécifiant la classe `String` pour leurs arguments de types génériques.
    
## <a name="linq-to-objects"></a>LINQ to Objects

La fonctionnalité LINQ to Objects permet aux développeurs d’utiliser des requêtes LINQ pour accéder aux objets en mémoire pour autant que le type d’objet implémente [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) ou [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1). Les requêtes LINQ fournissent un modèle commun pour accéder aux données, sont généralement plus concises et lisibles que les boucles foreach standard et intègrent des fonctions de filtrage, de classement et de regroupement. Pour plus d’informations, consultez [LINQ (Language-Integrated Query)](../../csharp/linq.md).

## <a name="see-also"></a>Voir aussi

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized)

[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[Collections thread-safe](threadsafe/index.md)



<!--HONumber=Nov16_HO1-->


