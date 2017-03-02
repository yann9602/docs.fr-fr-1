---
title: Types collection Hashtable et Dictionary
description: Types collection Hashtable et Dictionary
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0f18fac7-fd0d-4f25-a046-1d3d51de062e
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 58c87f9e86b5b97feb654e92a56f81940c201a6a
ms.lasthandoff: 03/02/2017

---

# <a name="hashtable-and-dictionary-collection-types"></a>Types collection Hashtable et Dictionary

La classe [System.Collections.Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) et les classes génériques [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) et [System.Collections.Concurrent.ConcurrentDictionary<T>](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) implémentent l’interface [System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary). La classe générique `Dictionary<T>` implémente également l’interface générique [IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2). Par conséquent, chaque élément de ces collections est une paire clé-valeur.

Un objet `Hashtable` est constitué de compartiments contenant les éléments de la collection. Un compartiment est un sous-groupe virtuel d'éléments dans la `Hashtable`, ce qui rend la recherche et la récupération plus facile et plus rapide que dans la plupart des collections. Chaque compartiment est associé à un code de hachage qui est généré à l'aide d'une fonction de hachage et qui est basé sur la clé de l'élément.

La classe générique [HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1) est une collection non ordonnée destinée à contenir des éléments uniques. 

Une fonction de hachage est un algorithme qui retourne un code de hachage numérique basé sur une clé. La clé est la valeur d'une propriété de l'objet stocké. Une fonction de hachage doit toujours retourner le même code de hachage pour la même clé. Il est possible pour une fonction de hachage pour générer le même code de hachage pour deux clés différentes, mais une fonction de hachage qui génère un code de hachage unique pour chaque clé unique produit de meilleures performances lors de la récupération des éléments dans la table de hachage.

Chaque objet qui est utilisé comme un élément dans une table `Hashtable` doit être en mesure de générer un code de hachage pour lui-même en utilisant une implémentation de la méthode `GetHashCode`. 

Quand un objet est ajouté à une table `Hashtable`, il est stocké dans le compartiment associé au code de hachage qui correspond au code de hachage de l'objet. Quand une valeur est recherchée dans la `Hashtable`, le code de hachage est généré pour cette valeur, et le compartiment associé à ce code de hachage est recherché.

Par exemple, une fonction de hachage pour une chaîne peut prendre les codes ASCII de chaque caractère de la chaîne et les additionner pour générer un code de hachage. La chaîne "pique-nique" aurait ainsi un code de hachage différent du code de hachage de la chaîne "basket". Les chaînes "pique-nique" et "basket" seraient donc dans des compartiments différents. Par contre, "ail" et "lia" auraient le même code de hachage et seraient dans le même compartiment.

Les classes `Dictionary<T>` et `ConcurrentDictionary<T>` ont les mêmes fonctionnalités que la classe `Hashtable`. Un dictionnaire `Dictionary<T>` d'un type spécifique (autre que `Object`) offre de meilleures performances qu'une table `Hashtable` pour les types valeur. La raison en est que les éléments de `Hashtable` sont de type `Object`. Par conséquent, le boxing et la conversion unboxing se produisent généralement quand vous stockez ou que vous récupérez un type valeur. La classe `ConcurrentDictionary<T>` doit être utilisée quand plusieurs threads sont susceptibles d’accéder simultanément à la collection.

## <a name="see-also"></a>Voir aussi

[Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable)

[IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)

[Dictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2)

[System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)

[System.Collections.Concurrent.ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2)

[Types de collections couramment utilisés](commonly-used-collection-types.md)


