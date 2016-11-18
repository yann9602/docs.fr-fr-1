---
title: "Types de collections triées"
description: "Types de collections triées"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bdc9c13e-e56a-433b-a293-c92364f6e9cb
translationtype: Human Translation
ms.sourcegitcommit: 149086110d7470d97e1ab3e5969269626290b523
ms.openlocfilehash: 4359ec4c55921497f32d5891ea337a30867e4fa5

---

# <a name="sorted-collection-types"></a>Types de collections triées  
 
 La classe [System.Collections.SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList), la classe générique [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) et la classe générique [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) sont similaires à la classe [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) et à la classe générique [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) dans la mesure où elles implémentent l’interface [IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary), mais elles conservent leurs éléments triés par clé et elles n’ont pas les caractéristiques de récupération et d’insertion O(1) des tables de hachage. Les trois classes ont plusieurs fonctionnalités en commun :  

 *   Les trois classes implémentent l’interface [System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary). Les deux classes génériques implémentent également l’interface générique [System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2).  
 
 *   Chaque élément est une paire clé/valeur utilisée à des fins d’énumération.   
  
> [!NOTE]  
> La classe [SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) non générique retourne des objets [DictionaryEntry](https://docs.microsoft.com/dotnet/core/api/System.Collections.DictionaryEntry) lorsqu’elle est énumérée, bien que les deux types génériques retournent des objets [KeyValuePair&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.KeyValuePair-2).  
   
*   Les éléments sont triés selon une implémentation [System.Collections.IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer) (pour la classe `SortedList` non générique) ou une implémentation [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) (pour les deux classes génériques).  
   
 *   Chaque classe fournit des propriétés qui retournent des collections contenant uniquement les clés ou uniquement les valeurs.  
   
Le tableau suivant répertorie certaines des différences entre les deux classes de liste triée et la classe [SortedDictionary<TKey, TValue>](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2).  
   
 `SortedList` (classe non générique) et `SortedList<TKey, TValue>` (classe générique) | `SortedDictionary<TKey, TValue>` (classe générique)  
 --------------------------------------------------------------------------------- | ------------------------------  
 Les propriétés qui retournent des clés et des valeurs sont indexées, ce qui permet une récupération indexée efficace. | Aucune récupération indexée.  
 La récupération est O(log n). | La récupération est O(log n).  
 L’insertion et la suppression sont généralement O(n). Toutefois, l’insertion est O(1) pour les données qui se trouvent déjà en ordre de tri, de sorte que chaque élément soit ajouté à la fin de la liste. (Cela suppose qu’un redimensionnement n’est pas requis.) | L’insertion et la suppression sont O(log n).  
 Utilise moins de mémoire qu’un `SortedDictionary<TKey, TValue>`. | Utilise plus de mémoire que la classe non générique `SortedList` et la classe générique `SortedList<TKey, TValue>`.  
  
 Pour les listes triées ou les dictionnaires qui doivent être accessibles simultanément à partir de plusieurs threads, vous pouvez ajouter une logique de tri à une classe qui dérive de [ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2).  
  
 > [!NOTE]  
 > Pour les valeurs qui contiennent leurs propres clés (par exemple, des enregistrements d’employés qui contiennent un ID d’employé), vous pouvez créer une collection à clé qui possède certaines caractéristiques d’une liste et certaines caractéristiques d’un dictionnaire en dérivant de la classe générique [KeyedCollection&lt;TKey, TItem&gt;]().  
   
 La classe [SortedSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedSet-1) fournit une arborescence auto-équilibrée qui maintient les données en ordre de tri après les insertions, les suppressions et les recherches. Cette classe et la classe [HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1) implémentent l’interface [ISet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ISet-1).  
   
## <a name="see-also"></a>Voir aussi  
  
[System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)  
   
[System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)  
   
[ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2)  
 
[Types de collection couramment utilisés](commonly-used-collection-types.md) 



<!--HONumber=Nov16_HO3-->


