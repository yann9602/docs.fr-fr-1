---
title: "Types de collections triées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: 16
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 210582c6cf31b59f7f6c4b577c0e8a2c2f25ddd6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="sorted-collection-types"></a><span data-ttu-id="df73a-102">Types de collections triées</span><span class="sxs-lookup"><span data-stu-id="df73a-102">Sorted Collection Types</span></span>
<span data-ttu-id="df73a-103">La classe <xref:System.Collections.SortedList?displayProperty=fullName>, la classe générique <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> et la classe générique <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> sont similaires à la classe <xref:System.Collections.Hashtable> et à la classe générique <xref:System.Collections.Generic.Dictionary%602>, car elles implémentent l’interface <xref:System.Collections.IDictionary>, mais conservent leurs éléments triés par clé et ne possèdent pas les caractéristiques d’insertion ni de récupération O(1) des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="df73a-103">The <xref:System.Collections.SortedList?displayProperty=fullName> class, the <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> generic class, and the <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> generic class are similar to the <xref:System.Collections.Hashtable> class and the <xref:System.Collections.Generic.Dictionary%602> generic class in that they implement the <xref:System.Collections.IDictionary> interface, but they maintain their elements in sort order by key, and they do not have the O(1) insertion and retrieval characteristic of hash tables.</span></span> <span data-ttu-id="df73a-104">Les trois classes ont plusieurs fonctionnalités en commun :</span><span class="sxs-lookup"><span data-stu-id="df73a-104">The three classes have several features in common:</span></span>  
  
-   <span data-ttu-id="df73a-105">Les trois classes implémentent toutes l’interface <xref:System.Collections.IDictionary?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="df73a-105">All three classes implement the <xref:System.Collections.IDictionary?displayProperty=fullName> interface.</span></span> <span data-ttu-id="df73a-106">Les deux classes génériques implémentent également l’interface générique <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="df73a-106">The two generic classes also implement the <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName> generic interface.</span></span>  
  
-   <span data-ttu-id="df73a-107">Chaque élément est une paire clé/valeur utilisée à des fins d’énumération.</span><span class="sxs-lookup"><span data-stu-id="df73a-107">Each element is a key/value pair for enumeration purposes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df73a-108">La classe <xref:System.Collections.SortedList> non générique retourne des objets <xref:System.Collections.DictionaryEntry> quand elle est énumérée, même si les deux types génériques retournent des objets <xref:System.Collections.Generic.KeyValuePair%602>.</span><span class="sxs-lookup"><span data-stu-id="df73a-108">The nongeneric <xref:System.Collections.SortedList> class returns <xref:System.Collections.DictionaryEntry> objects when enumerated, although the two generic types return <xref:System.Collections.Generic.KeyValuePair%602> objects.</span></span>  
  
-   <span data-ttu-id="df73a-109">Les éléments sont triés selon une implémentation d’<xref:System.Collections.IComparer?displayProperty=fullName> (pour la classe <xref:System.Collections.SortedList> non générique) ou une implémentation d’<xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> (pour les deux classes génériques).</span><span class="sxs-lookup"><span data-stu-id="df73a-109">Elements are sorted according to a <xref:System.Collections.IComparer?displayProperty=fullName> implementation (for nongeneric <xref:System.Collections.SortedList>) or a <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> implementation (for the two generic classes).</span></span>  
  
-   <span data-ttu-id="df73a-110">Chaque classe fournit des propriétés qui retournent des collections contenant uniquement les clés ou uniquement les valeurs.</span><span class="sxs-lookup"><span data-stu-id="df73a-110">Each class provides properties that return collections containing only the keys or only the values.</span></span>  
  
 <span data-ttu-id="df73a-111">Le tableau suivant répertorie certaines des différences entre les deux classes de liste triée et la classe <xref:System.Collections.Generic.SortedDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="df73a-111">The following table lists some of the differences between the two sorted list classes and the <xref:System.Collections.Generic.SortedDictionary%602> class.</span></span>  
  
|<span data-ttu-id="df73a-112"><xref:System.Collections.SortedList> (classe non générique) et <xref:System.Collections.Generic.SortedList%602> (classe générique)</span><span class="sxs-lookup"><span data-stu-id="df73a-112"><xref:System.Collections.SortedList> nongeneric class and <xref:System.Collections.Generic.SortedList%602> generic class</span></span>|<span data-ttu-id="df73a-113"><xref:System.Collections.Generic.SortedDictionary%602> (classe générique)</span><span class="sxs-lookup"><span data-stu-id="df73a-113"><xref:System.Collections.Generic.SortedDictionary%602> generic class</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="df73a-114">Les propriétés qui retournent des clés et des valeurs sont indexées, ce qui permet une récupération indexée efficace.</span><span class="sxs-lookup"><span data-stu-id="df73a-114">The properties that return keys and values are indexed, allowing efficient indexed retrieval.</span></span>|<span data-ttu-id="df73a-115">Aucune récupération indexée.</span><span class="sxs-lookup"><span data-stu-id="df73a-115">No indexed retrieval.</span></span>|  
|<span data-ttu-id="df73a-116">La récupération est O(log `n`).</span><span class="sxs-lookup"><span data-stu-id="df73a-116">Retrieval is O(log `n`).</span></span>|<span data-ttu-id="df73a-117">La récupération est O(log `n`).</span><span class="sxs-lookup"><span data-stu-id="df73a-117">Retrieval is O(log `n`).</span></span>|  
|<span data-ttu-id="df73a-118">L’insertion et la suppression correspondent généralement à O(`n`). Toutefois, l’insertion correspond à O(log `n`) pour les données qui se trouvent déjà en ordre de tri, afin que chaque élément soit ajouté à la fin de la liste.</span><span class="sxs-lookup"><span data-stu-id="df73a-118">Insertion and removal are generally O(`n`); however, insertion is O(log `n`) for data that are already in sort order, so that each element is added to the end of the list.</span></span> <span data-ttu-id="df73a-119">(Cela suppose qu’un redimensionnement n’est pas requis.)</span><span class="sxs-lookup"><span data-stu-id="df73a-119">(This assumes that a resize is not required.)</span></span>|<span data-ttu-id="df73a-120">L’insertion et la suppression sont O(log `n`).</span><span class="sxs-lookup"><span data-stu-id="df73a-120">Insertion and removal are O(log `n`).</span></span>|  
|<span data-ttu-id="df73a-121">Utilise moins de mémoire qu’un <xref:System.Collections.Generic.SortedDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="df73a-121">Uses less memory than a <xref:System.Collections.Generic.SortedDictionary%602>.</span></span>|<span data-ttu-id="df73a-122">Utilise plus de mémoire que la classe non générique <xref:System.Collections.SortedList> et la classe générique <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="df73a-122">Uses more memory than the <xref:System.Collections.SortedList> nongeneric class and the <xref:System.Collections.Generic.SortedList%602> generic class.</span></span>|  
  
 <span data-ttu-id="df73a-123">Pour les listes ou les dictionnaires triés qui doivent être accessibles simultanément à partir de plusieurs threads, vous pouvez ajouter une logique de tri à une classe qui dérive de <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="df73a-123">For sorted lists or dictionaries that must be accessible concurrently from multiple threads, you can add sorting logic to a class that derives from <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df73a-124">Pour les valeurs qui contiennent leurs propres clés (par exemple, des enregistrements d’employés qui contiennent un numéro d’ID de l’employé), vous pouvez créer une collection à clé qui possède certaines caractéristiques d’une liste et certaines caractéristiques d’un dictionnaire en dérivant de la classe générique <xref:System.Collections.ObjectModel.KeyedCollection%602>.</span><span class="sxs-lookup"><span data-stu-id="df73a-124">For values that contain their own keys (for example, employee records that contain an employee ID number), you can create a keyed collection that has some characteristics of a list and some characteristics of a dictionary by deriving from the <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class.</span></span>  
  
 <span data-ttu-id="df73a-125">À partir de [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la classe <xref:System.Collections.Generic.SortedSet%601> fournit une arborescence autonome qui maintient les données triées dans un certain ordre après les insertions, les suppressions et les recherches.</span><span class="sxs-lookup"><span data-stu-id="df73a-125">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the <xref:System.Collections.Generic.SortedSet%601> class provides a self-balancing tree that maintains data in sorted order after insertions, deletions, and searches.</span></span> <span data-ttu-id="df73a-126">Cette classe et la classe <xref:System.Collections.Generic.HashSet%601> implémentent l’interface <xref:System.Collections.Generic.ISet%601>.</span><span class="sxs-lookup"><span data-stu-id="df73a-126">This class and the <xref:System.Collections.Generic.HashSet%601> class implement the <xref:System.Collections.Generic.ISet%601> interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df73a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df73a-127">See Also</span></span>  
 <span data-ttu-id="df73a-128"><xref:System.Collections.IDictionary?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="df73a-128"><xref:System.Collections.IDictionary?displayProperty=fullName></span></span>   
 <span data-ttu-id="df73a-129"><xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="df73a-129"><xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName></span></span>   
 <span data-ttu-id="df73a-130"><xref:System.Collections.Concurrent.ConcurrentDictionary%602></span><span class="sxs-lookup"><span data-stu-id="df73a-130"><xref:System.Collections.Concurrent.ConcurrentDictionary%602></span></span>   
 [<span data-ttu-id="df73a-131">Types de collections couramment utilisés</span><span class="sxs-lookup"><span data-stu-id="df73a-131">Commonly Used Collection Types</span></span>](../../../docs/standard/collections/commonly-used-collection-types.md)

