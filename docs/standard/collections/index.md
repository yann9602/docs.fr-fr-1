---
title: "Collections et structures de donn&#233;es | Microsoft Docs"
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
  - "regrouper des données dans des collections"
  - "objets (.NET Framework), regroupement dans des collections"
  - "Array (classe), regroupement de données dans des collections"
  - "threads (.NET Framework), sécurité"
  - "classes de collections"
  - "collections (.NET Framework)"
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
caps.latest.revision: 36
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 35
---
# Collections et structures de donn&#233;es
Des données similaires peuvent souvent être gérées plus efficacement quand elles sont stockées et manipulées en tant que collection. Vous pouvez utiliser la <xref:System.Array?displayProperty=fullName> classe ou les classes dans le <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, System.Collections.Immutable des espaces de noms à ajouter, supprimer et modifier des éléments individuels ou une plage d’éléments dans une collection.  
  
 Il existe deux principaux types de collections : les collections génériques et non génériques. Les collections génériques ont été ajoutées au .NET Framework 2.0 et fournissent des collections de type sécurisé au moment de la compilation. Pour cette raison, les collections génériques offrent généralement de meilleures performances. Les collections génériques acceptent un paramètre de type lorsqu’elles sont construites, et ne nécessitent pas de transtypage du type <xref:System.Object> quand vous ajoutez ou supprimez des éléments de la collection.  De plus, la plupart des collections génériques sont prises en charge par les applications du [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)]. Les collections non génériques stockent les éléments en tant que <xref:System.Object>, nécessitent un transtypage, et la plupart n’est pas pris en charge pour [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] développement d’applications. Cependant, vous pouvez rencontrer ces collections non génériques dans du code plus ancien.  
  
 Compter les [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], les collections de la <xref:System.Collections.Concurrent> espace de noms fournissent des opérations thread-safe efficaces pour accéder aux éléments de la collection à partir de plusieurs threads. Les classes de collection immuables dans l’espace de noms System.Collections.Immutable ([package NuGet](https://www.nuget.org/packages/System.Collections.Immutable)) sont thread-safe, car les opérations sont effectuées sur une copie de la collection d’origine et la collection d’origine ne peut pas être modifiée.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Fonctionnalités communes à toutes les collections  
 Toutes les collections fournissent des méthodes pour l'ajout, la suppression ou la recherche d'éléments au sein d'une collection. En outre, toutes les collections qui implémentent directement ou indirectement la <xref:System.Collections.ICollection> interface ou le <xref:System.Collections.Generic.ICollection%601> partagent ces fonctionnalités :  
  
-   **Possibilité d'énumérer la collection**  
  
     Collections de .NET framework implémentent soit <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> pour activer la collecte d’être parcourue. Un énumérateur peut être vu comme un pointeur mobile pointant vers n'importe quel élément d'une collection. Le [foreach, dans](../Topic/foreach,%20in%20\(C%23%20Reference\).md) instruction et le [For Each... L’instruction suivante](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md) utilisent l’énumérateur exposé par le <xref:System.Collections.IEnumerable.GetEnumerator%2A> méthode et masquent la complexité de manipuler l’énumérateur. En outre, toute collection qui implémente <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> est considéré comme un *type requêtable* et peut être interrogée avec LINQ. Les requêtes LINQ fournissent un modèle commun d'accès aux données. Elles sont généralement plus concises et lisibles que les boucles `foreach` standard, et fournissent des fonctionnalités de filtrage, de tri et de regroupement. Les requêtes LINQ peuvent également améliorer les performances. Pour plus d’informations, consultez [LINQ to Objects](../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md) et [Introduction aux requêtes LINQ (c#)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md).  
  
-   **La possibilité de copier le contenu d'une collection dans un tableau**  
  
     Toutes les collections peuvent être copiées vers un tableau à l’aide de la **CopyTo** méthode ; Toutefois, l’ordre des éléments dans le nouveau tableau est basé sur la séquence dans laquelle l’énumérateur les retourne. Le tableau résultant est toujours unidimensionnel avec une limite inférieure de zéro.  
  
 De plus, de nombreuses classes de collection comprennent les fonctionnalités suivantes :  
  
-   **Propriétés Capacity et Count**  
  
     La propriété Capacity d'une collection indique le nombre d'éléments qu'elle peut contenir. La propriété Count d'une collection indique le nombre d'éléments qu'elle contient réellement. Certaines collections masquent l'une de ces propriétés, voire les deux.  
  
     La capacité de la plupart des collections s'étend automatiquement quand la valeur de la propriété Capacity est atteinte. La mémoire est réallouée et les éléments sont copiés depuis l'ancienne collection vers la nouvelle. Cela permet de réduire le code nécessaire à l'utilisation de la collection. Toutefois, les performances de la collection peuvent être affectées. Par exemple, pour <xref:System.Collections.Generic.List%601>si <xref:System.Collections.Generic.List%601.Count%2A> est inférieure à <xref:System.Collections.Generic.List%601.Capacity%2A>, l’ajout d’un élément est une opération o (1). Si la capacité doit être augmentée pour intégrer le nouvel élément, l’ajout d’un élément devient une opération o (n), où n est <xref:System.Collections.Generic.List%601.Count%2A>. Le meilleur moyen d'éviter la dégradation des performances en raison des réallocations est de définir la propriété Capacity sur la taille estimée de la collection.  
  
     <xref:System.Collections.BitArray> est un cas particulier. Sa capacité est égale à sa longueur, qui est elle-même égale à son décompte.  
  
-   **Une limite inférieure cohérente**  
  
     La limite inférieure d'une collection est l'index de son premier élément. Toutes les collections indexées dans l’espace de noms <xref:System.Collections> ont une limite inférieure de zéro, ce qui signifie qu’elles sont indexées à 0. <xref:System.Array> a une limite inférieure de zéro par défaut, mais une limite inférieure différente peut être définie lors de la création d’une instance de la **tableau** à l’aide de la classe <xref:System.Array.CreateInstance%2A?displayProperty=fullName>.  
  
-   **Synchronisation pour un accès depuis plusieurs threads** (classes <xref:System.Collections> uniquement).  
  
     Types de collections non génériques dans le <xref:System.Collections> espace de noms fournissent une certaine sécurité thread avec la synchronisation, généralement exposée par le <xref:System.Collections.ICollection.SyncRoot%2A> et <xref:System.Collections.ICollection.IsSynchronized%2A> membres. Ces collections ne sont pas thread-safe par défaut. Si vous avez besoin d’un accès multithread évolutif et efficace pour une collection, utilisez l’une des classes de l’espace de noms <xref:System.Collections.Concurrent> ou envisagez d’utiliser une collection immuable. Pour plus d’informations, consultez [Collections thread-safe](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Choix d'une collection  
 En règle générale, vous devez utiliser des collections génériques. Le tableau suivant décrit certains scénarios courants concernant les collections, ainsi que les classes de collection que vous pouvez utiliser pour ces scénarios. Si vous ne connaissez pas encore les collections génériques, ce tableau vous aidera à choisir la collection générique qui répond le mieux à vos besoins.  
  
|||||  
|-|-|-|-|  
|Je souhaite :|Option(s) de collection générique|Option(s) de collection non générique|Option(s) de collection thread-safe ou immuable|  
|Stocker les éléments sous forme de paires clé/valeur pour une recherche rapide par clé|<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName></TKey, TValue>|<xref:System.Collections.Hashtable><br /><br /> (collection de paires clé/valeur organisées en fonction du code de hachage de la clé).|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>\</TKey, TValue><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=fullName>\</TKey, TValue><br /><br /> [Classe de ImmutableDictionary (TKey, TValue)](../Topic/ImmutableDictionary\(TKey,%20TValue\)%20Class.md)|  
|Accéder aux éléments par index|<xref:System.Collections.Generic.List%601?displayProperty=fullName>|<xref:System.Array?displayProperty=fullName><br /><br /> <xref:System.Collections.ArrayList?displayProperty=fullName>|[ImmutableList(T) (classe)](../Topic/ImmutableList\(T\)%20Class.md)<br /><br /> [ImmutableArray (classe)](../Topic/ImmutableArray%20Class.md)|  
|Utiliser des éléments premier entré, premier sorti (FIFO)|<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>|<xref:System.Collections.Queue?displayProperty=fullName>|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName><br /><br /> [ImmutableQueue(T) (classe)](../Topic/ImmutableQueue\(T\)%20Class.md)|  
|Utiliser des données dernier entré, premier sorti (LIFO)|<xref:System.Collections.Generic.Stack%601?displayProperty=fullName>|<xref:System.Collections.Stack?displayProperty=fullName>|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName><br /><br /> [ImmutableStack(T) (classe)](../Topic/ImmutableStack\(T\)%20Class.md)|  
|Accéder aux éléments de manière séquentielle|<xref:System.Collections.Generic.LinkedList%601?displayProperty=fullName>|Aucune recommandation|Aucune recommandation|  
|Recevoir des notifications quand des éléments sont supprimés ou ajoutés à la collection. (implémente <xref:System.ComponentModel.INotifyPropertyChanged> et <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=fullName>)|<xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=fullName>|Aucune recommandation|Aucune recommandation|  
|Collection triée|<xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>\</TKey, TValue>|<xref:System.Collections.SortedList?displayProperty=fullName>|[Classe de ImmutableSortedDictionary (TKey, TValue)](../Topic/ImmutableSortedDictionary\(TKey,%20TValue\)%20Class.md)<br /><br /> [ImmutableSortedSet(T) (classe)](../Topic/ImmutableSortedSet\(T\)%20Class.md)|  
|Ensemble de fonctions mathématiques|<xref:System.Collections.Generic.HashSet%601?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName>|Aucune recommandation|[ImmutableHashSet(T) (classe)](../Topic/ImmutableHashSet\(T\)%20Class.md)<br /><br /> [ImmutableSortedSet(T) (classe)](../Topic/ImmutableSortedSet\(T\)%20Class.md)|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Sélection d’une classe de collection](../../../docs/standard/collections/selecting-a-collection-class.md)|Décrit les différentes collections et permet d'en sélectionner une pour votre scénario.|  
|[Types de collections couramment utilisés](../../../docs/standard/collections/commonly-used-collection-types.md)|Décrit les types de collection génériques et non génériques fréquemment utilisés, tels que <xref:System.Array?displayProperty=fullName>, <xref:System.Collections.Generic.List%601?displayProperty=fullName>, et <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>.\</TKey, TValue>|  
|[Quand utiliser les collections génériques](../../../docs/standard/collections/when-to-use-generic-collections.md)|Traite de l'utilisation des types de collections génériques.|  
|[Comparaisons et tris dans les collections](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Aborde l'utilisation des comparaisons d'égalité et de tri dans les collections.|  
|[Types de collections triées](../../../docs/standard/collections/sorted-collection-types.md)|Aborde les caractéristiques et les performances des collections triées.|  
|[Types de collections Hashtable et Dictionary](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Décrit les fonctionnalités des types de dictionnaires basés sur le hachage génériques et non génériques.|  
|[Collections thread-safe](../../../docs/standard/collections/thread-safe/index.md)|Décrit les types de collections tels que <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> et <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> qui prennent en charge un accès simultané sécurisé et efficace de plusieurs threads.|  
|System.Collections.Immutable|Présente les collections immuables et fournit des liens vers les types de collection.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Référence  
 <xref:System.Array?displayProperty=fullName>  
  
 <xref:System.Collections?displayProperty=fullName>  
  
 <xref:System.Collections.Concurrent?displayProperty=fullName>  
  
 <xref:System.Collections.Generic?displayProperty=fullName>  
  
 <xref:System.Collections.Specialized?displayProperty=fullName>  
  
 <xref:System.Linq?displayProperty=fullName>  
  
 System.Collections.Immutable