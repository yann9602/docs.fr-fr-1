---
title: "Comment : implémenter un partitionneur pour un partitionnement statique"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b28ff0bb8436fefc4956918889435e258ae98b12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="ccef8-102">Comment : implémenter un partitionneur pour un partitionnement statique</span><span class="sxs-lookup"><span data-stu-id="ccef8-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="ccef8-103">L’exemple suivant montre une façon d’implémenter un partitionneur personnalisé simple pour PLINQ qui exécute le partitionnement statique.</span><span class="sxs-lookup"><span data-stu-id="ccef8-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="ccef8-104">Étant donné que le partitionneur ne prend pas en charge les partitions dynamiques, il n’est pas utilisable à partir de <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ccef8-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ccef8-105">Ce partitionneur particulier peut fournir une accélération sur le partitionneur de plage par défaut pour les sources de données pour laquelle chaque élément requiert une quantité croissante de temps de traitement.</span><span class="sxs-lookup"><span data-stu-id="ccef8-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccef8-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="ccef8-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="ccef8-107">Les partitions dans cet exemple sont basées sur l’hypothèse d’une augmentation linéaire du temps de traitement pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="ccef8-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="ccef8-108">Dans le monde réel, il peut être difficile à prédire le temps de traitement de cette façon.</span><span class="sxs-lookup"><span data-stu-id="ccef8-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="ccef8-109">Si vous utilisez un partitionneur statique avec une source de données spécifique, vous pouvez optimiser la formule de partitionnement pour la source, ajouter la logique de l’équilibrage de charge ou utiliser un bloc de méthode de partitionnement, comme illustré dans [Comment : implémenter des Partitions dynamiques](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="ccef8-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccef8-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccef8-110">See Also</span></span>  
 [<span data-ttu-id="ccef8-111">Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)</span><span class="sxs-lookup"><span data-stu-id="ccef8-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
