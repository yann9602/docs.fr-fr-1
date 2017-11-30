---
title: "Comment : accélérer les petits corps de boucles"
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
helpviewer_keywords: parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d38d8beedf342720d4dc68026297edb457f5ed35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="c7e84-102">Comment : accélérer les petits corps de boucles</span><span class="sxs-lookup"><span data-stu-id="c7e84-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="c7e84-103">Lorsqu’un <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> boucle avec un petit corps, peuvent s’exécuter plus lentement que les boucles séquentielles équivalentes, telles que la [pour](~/docs/csharp/language-reference/keywords/for.md) boucle en c# et la [pour](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c7e84-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](~/docs/csharp/language-reference/keywords/for.md) loop in C# and the [For](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) loop in Visual Basic.</span></span> <span data-ttu-id="c7e84-104">La baisse des performances est provoquée par les surcharges impliquées dans le partitionnement des données et par le coût de l'appel d'un délégué sur chaque itération de boucle.</span><span class="sxs-lookup"><span data-stu-id="c7e84-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="c7e84-105">Pour résoudre ces scénarios, la classe <xref:System.Collections.Concurrent.Partitioner> offre la méthode <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>, ce qui vous permet de fournir une boucle séquentielle pour le corps du délégué, afin que celui-ci soit appelé une seule fois par partition, au lieu d'une fois par itération.</span><span class="sxs-lookup"><span data-stu-id="c7e84-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="c7e84-106">Pour plus d’informations, consultez [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="c7e84-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7e84-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7e84-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="c7e84-108">L'approche illustrée dans cet exemple est utile quand la boucle exécute une quantité minimale de travail.</span><span class="sxs-lookup"><span data-stu-id="c7e84-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="c7e84-109">À mesure que le travail devient de plus en plus gourmand en ressources informatiques, vous obtiendrez probablement des performances identiques ou meilleures en utilisant une boucle <xref:System.Threading.Tasks.Parallel.For%2A> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> avec le partitionneur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c7e84-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e84-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7e84-110">See Also</span></span>  
 [<span data-ttu-id="c7e84-111">Parallélisme de données</span><span class="sxs-lookup"><span data-stu-id="c7e84-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="c7e84-112">Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)</span><span class="sxs-lookup"><span data-stu-id="c7e84-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="c7e84-113">Itérateurs</span><span class="sxs-lookup"><span data-stu-id="c7e84-113">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="c7e84-114">Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="c7e84-114">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
