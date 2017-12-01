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
# <a name="how-to-implement-dynamic-partitions"></a>Comment : implémenter des partitions dynamiques
L’exemple suivant montre comment implémenter un <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> qui implémente le partitionnement dynamique et peut être utilisée à partir de certaines surcharges <xref:System.Threading.Tasks.Parallel.ForEach%2A> et à partir de PLINQ.  
  
## <a name="example"></a>Exemple  
 Chaque fois qu’une partition appelle <xref:System.Collections.IEnumerator.MoveNext%2A> sur l’énumérateur, l’énumérateur fournit la partition avec un élément de liste. Dans le cas de PLINQ et <xref:System.Threading.Tasks.Parallel.ForEach%2A>, la partition est un <xref:System.Threading.Tasks.Task> instance. Étant donné que les requêtes arrivent simultanément sur plusieurs threads, l’accès à l’index actuel est synchronisé.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 Il s’agit d’un exemple de partitionnement par segments, avec chaque segment qui se compose d’un seul élément. En fournissant plus d’éléments à la fois, vous pourriez réduire le conflit sur le verrou et théoriquement atteindre des performances plus rapides. Toutefois, à un moment donné, blocs plus volumineux peuvent nécessiter une logique supplémentaire l’équilibrage de charge afin de conserver tous les threads occupés jusqu'à ce que tout le travail est effectué.  
  
## <a name="see-also"></a>Voir aussi  
 [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Guide pratique pour implémenter un partitionneur pour un partitionnement statique](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
