---
title: "Comment : synchroniser des opérations simultanées avec un objet Barrier"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Comment : synchroniser des opérations simultanées avec un objet Barrier
L’exemple suivant montre comment synchroniser des tâches simultanées avec un <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Exemple  
 L’objectif du programme suivant est pour compter le nombre itérations (ou phases) sont requis pour deux threads trouvent leur moitié de la solution sur la même phase à l’aide d’un algorithme aléatoire remanier les mots. Une fois que chaque thread a mélangé ses mots, l’opération post-phase de cloisonnement compare les deux résultats pour voir si la phrase complète a été restituée dans l’ordre correct des mots.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> est un objet qui empêche des tâches individuelles dans une opération parallèle de se poursuivre jusqu'à ce que toutes les tâches atteignent le cloisonnement. Il est utile lorsqu’une opération parallèle se produit en plusieurs phases, et chaque phase requiert la synchronisation entre les tâches. Dans cet exemple, il existe deux phases à l’opération. Dans la première phase, chaque tâche remplit sa section de la mémoire tampon avec des données. Lors de chaque tâche a rempli sa section, la tâche signale le cloisonnement qu’il est prêt à continuer, puis attend. Lorsque toutes les tâches ont signalé le cloisonnement, elles sont débloqués et la deuxième phase démarre. Le cloisonnement est nécessaire car la deuxième phase requiert que chaque tâche ait accès à toutes les données qui a été généré pour ce point. Sans le cloisonnement, les premières tâches à effectuer peuvent tenter de lire à partir de mémoires tampons qui les n'ont pas encore été remplies par d’autres tâches. Vous pouvez synchroniser n’importe quel nombre de phases de cette manière.  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de données pour la programmation parallèle](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
