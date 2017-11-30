---
title: "Comment : implémenter des partitions dynamiques"
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
helpviewer_keywords: tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1e5dc93997918e0f7da29fa1f94c434a556f19f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="f1df9-102">Comment : implémenter des partitions dynamiques</span><span class="sxs-lookup"><span data-stu-id="f1df9-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="f1df9-103">L’exemple suivant montre comment implémenter un <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> qui implémente le partitionnement dynamique et peut être utilisée à partir de certaines surcharges <xref:System.Threading.Tasks.Parallel.ForEach%2A> et à partir de PLINQ.</span><span class="sxs-lookup"><span data-stu-id="f1df9-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1df9-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f1df9-104">Example</span></span>  
 <span data-ttu-id="f1df9-105">Chaque fois qu’une partition appelle <xref:System.Collections.IEnumerator.MoveNext%2A> sur l’énumérateur, l’énumérateur fournit la partition avec un élément de liste.</span><span class="sxs-lookup"><span data-stu-id="f1df9-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="f1df9-106">Dans le cas de PLINQ et <xref:System.Threading.Tasks.Parallel.ForEach%2A>, la partition est un <xref:System.Threading.Tasks.Task> instance.</span><span class="sxs-lookup"><span data-stu-id="f1df9-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="f1df9-107">Étant donné que les requêtes arrivent simultanément sur plusieurs threads, l’accès à l’index actuel est synchronisé.</span><span class="sxs-lookup"><span data-stu-id="f1df9-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="f1df9-108">Il s’agit d’un exemple de partitionnement par segments, avec chaque segment qui se compose d’un seul élément.</span><span class="sxs-lookup"><span data-stu-id="f1df9-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="f1df9-109">En fournissant plus d’éléments à la fois, vous pourriez réduire le conflit sur le verrou et théoriquement atteindre des performances plus rapides.</span><span class="sxs-lookup"><span data-stu-id="f1df9-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="f1df9-110">Toutefois, à un moment donné, blocs plus volumineux peuvent nécessiter une logique supplémentaire l’équilibrage de charge afin de conserver tous les threads occupés jusqu'à ce que tout le travail est effectué.</span><span class="sxs-lookup"><span data-stu-id="f1df9-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1df9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1df9-111">See Also</span></span>  
 [<span data-ttu-id="f1df9-112">Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)</span><span class="sxs-lookup"><span data-stu-id="f1df9-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="f1df9-113">Guide pratique pour implémenter un partitionneur pour un partitionnement statique</span><span class="sxs-lookup"><span data-stu-id="f1df9-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
