---
title: Comparaisons et tris dans les collections
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 826adbecfc6a57b05db482766baae397ce72bc9d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="5e5c2-102">Comparaisons et tris dans les collections</span><span class="sxs-lookup"><span data-stu-id="5e5c2-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="5e5c2-103">Les classes <xref:System.Collections> effectuent des comparaisons dans quasiment tous les processus impliqués dans la gestion des collections, que ce soit pendant la recherche d'un élément à supprimer ou le renvoi d'une valeur d'une paire clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="5e5c2-104">Les collections utilisent généralement un comparateur d'égalité et/ou un comparateur de classement.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="5e5c2-105">Deux constructions sont utilisées pour les comparaisons.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a><span data-ttu-id="5e5c2-106">Vérification de l'égalité</span><span class="sxs-lookup"><span data-stu-id="5e5c2-106">Checking for equality</span></span>  
 <span data-ttu-id="5e5c2-107">Les méthodes telles que `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>et `Remove` utilisent un comparateur d'égalité pour les éléments de collection.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="5e5c2-108">Si la collection est générique, les éléments font l'objet d'une comparaison d'égalité, selon les consignes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5e5c2-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
-   <span data-ttu-id="5e5c2-109">Si le type T implémente l'interface générique <xref:System.IEquatable%601> , le comparateur d'égalité est la méthode <xref:System.IEquatable%601.Equals%2A> de cette interface.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
-   <span data-ttu-id="5e5c2-110">Si le type T n'implémente pas <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>  
  
 <span data-ttu-id="5e5c2-111">De plus, certaines surcharges de constructeur pour les collections de dictionnaires acceptent une implémentation <xref:System.Collections.Generic.IEqualityComparer%601> , qui est utilisée pour comparer l'égalité de clés.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-111">In addition, Some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="5e5c2-112">Pour obtenir un exemple, consultez le constructeur <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e5c2-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a><span data-ttu-id="5e5c2-113">Détermination de l'ordre de tri</span><span class="sxs-lookup"><span data-stu-id="5e5c2-113">Determining sort order</span></span>  
 <span data-ttu-id="5e5c2-114">Les méthodes telles que `BinarySearch` et `Sort` utilisent un comparateur de classement pour les éléments de collection.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="5e5c2-115">Les comparaisons peuvent être effectuées entre les éléments d'une collection, ou entre un élément et une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="5e5c2-116">Pour comparer des objets, il existe le `default comparer` et le `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="5e5c2-117">Le comparateur par défaut repose sur au moins l'un des objets comparés pour implémenter l'interface **IComparable** .</span><span class="sxs-lookup"><span data-stu-id="5e5c2-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="5e5c2-118">Il est recommandé d'implémenter **IComparable** sur toutes les classes utilisées en tant que valeurs dans une collection de listes ou en tant que clés dans une collection de dictionnaires.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="5e5c2-119">Pour une collection générique, la comparaison d’égalité est déterminée selon ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="5e5c2-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
-   <span data-ttu-id="5e5c2-120">Si le type T implémente l'interface générique <xref:System.IComparable%601?displayProperty=nameWithType> , le comparateur par défaut est la méthode <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> de cette interface.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>  
  
-   <span data-ttu-id="5e5c2-121">Si le type T implémente l'interface non générique <xref:System.IComparable?displayProperty=nameWithType> , le comparateur par défaut est la méthode <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> de cette interface.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>  
  
-   <span data-ttu-id="5e5c2-122">Si le type T n'implémente aucune interface, il n'existe aucun comparateur par défaut. Un comparateur ou un délégué de comparaison doit donc être fourni explicitement.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="5e5c2-123">Pour fournir des comparaisons explicites, certaines méthodes acceptent une implémentation **IComparer** en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="5e5c2-124">Par exemple, la méthode <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> accepte une implémentation <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e5c2-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>  
  
 <span data-ttu-id="5e5c2-125">Le paramètre de culture actuel du système peut affecter les comparaisons et les tris d’une collection.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="5e5c2-126">Par défaut, les comparaisons et les tris des classes **Collections** sont dépendants de la culture.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="5e5c2-127">Pour ignorer le paramètre de culture et donc obtenir des résultats cohérents de comparaison et de tri, utilisez <xref:System.Globalization.CultureInfo.InvariantCulture%2A> avec des surcharges de membre qui acceptent <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="5e5c2-128">Pour plus d’informations, consultez [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) et [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="5e5c2-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a><span data-ttu-id="5e5c2-129">Exemple d'égalité et de tri</span><span class="sxs-lookup"><span data-stu-id="5e5c2-129">Equality and sort example</span></span>  
 <span data-ttu-id="5e5c2-130">Le code suivant illustre une implémentation de <xref:System.IEquatable%601> et de <xref:System.IComparable%601> dans un objet métier simple.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="5e5c2-131">De plus, quand l'objet est stocké dans une liste, puis trié, vous verrez que l'appel de la méthode <xref:System.Collections.Generic.List%601.Sort> se traduit par l'utilisation du comparateur par défaut pour le type `Part` , et par l'implémentation de la méthode <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> à l'aide d'une méthode anonyme.</span><span class="sxs-lookup"><span data-stu-id="5e5c2-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5e5c2-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e5c2-132">See Also</span></span>  
 <xref:System.Collections.IComparer>  
 <xref:System.IEquatable%601>  
 <xref:System.Collections.Generic.IComparer%601>  
 <xref:System.IComparable>  
 <xref:System.IComparable%601>
