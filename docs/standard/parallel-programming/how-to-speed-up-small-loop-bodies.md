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
# <a name="how-to-speed-up-small-loop-bodies"></a>Comment : accélérer les petits corps de boucles
Lorsqu’un <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> boucle avec un petit corps, peuvent s’exécuter plus lentement que les boucles séquentielles équivalentes, telles que la [pour](~/docs/csharp/language-reference/keywords/for.md) boucle en c# et la [pour](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) en Visual Basic. La baisse des performances est provoquée par les surcharges impliquées dans le partitionnement des données et par le coût de l'appel d'un délégué sur chaque itération de boucle. Pour résoudre ces scénarios, la classe <xref:System.Collections.Concurrent.Partitioner> offre la méthode <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>, ce qui vous permet de fournir une boucle séquentielle pour le corps du délégué, afin que celui-ci soit appelé une seule fois par partition, au lieu d'une fois par itération. Pour plus d’informations, consultez [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 L'approche illustrée dans cet exemple est utile quand la boucle exécute une quantité minimale de travail. À mesure que le travail devient de plus en plus gourmand en ressources informatiques, vous obtiendrez probablement des performances identiques ou meilleures en utilisant une boucle <xref:System.Threading.Tasks.Parallel.For%2A> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> avec le partitionneur par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Parallélisme de données](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
