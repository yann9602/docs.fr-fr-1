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
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Comment : implémenter un partitionneur pour un partitionnement statique
L’exemple suivant montre une façon d’implémenter un partitionneur personnalisé simple pour PLINQ qui exécute le partitionnement statique. Étant donné que le partitionneur ne prend pas en charge les partitions dynamiques, il n’est pas utilisable à partir de <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Ce partitionneur particulier peut fournir une accélération sur le partitionneur de plage par défaut pour les sources de données pour laquelle chaque élément requiert une quantité croissante de temps de traitement.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Les partitions dans cet exemple sont basées sur l’hypothèse d’une augmentation linéaire du temps de traitement pour chaque élément. Dans le monde réel, il peut être difficile à prédire le temps de traitement de cette façon. Si vous utilisez un partitionneur statique avec une source de données spécifique, vous pouvez optimiser la formule de partitionnement pour la source, ajouter la logique de l’équilibrage de charge ou utiliser un bloc de méthode de partitionnement, comme illustré dans [Comment : implémenter des Partitions dynamiques](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
