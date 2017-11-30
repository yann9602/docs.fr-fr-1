---
title: "Comment : utiliser le verrouillage spinlock pour une synchronisation de bas niveau"
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
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Comment : utiliser le verrouillage spinlock pour une synchronisation de bas niveau
L’exemple suivant montre comment utiliser un <xref:System.Threading.SpinLock>.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la section critique exécute une quantité minimale de travail, ce qui en fait un bon candidat pour un <xref:System.Threading.SpinLock>. Le travail une petite quantité d’augmenter les performances de la <xref:System.Threading.SpinLock> par rapport à un verrou standard. Toutefois, à un moment, le verrouillage tournant devient plus coûteux qu’un verrouillage standard. Vous pouvez utiliser la fonctionnalité de profilage d'accès concurrentiel dans les outils de profilage pour voir quel type de verrouillage offre les meilleures performances pour votre programme. Pour plus d’informations, consultez [Visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock>peut être utile lorsqu’un verrou sur une ressource partagée ne va pas être maintenu pendant très long. Dans ce cas, sur les ordinateurs multicœurs, le thread bloqué peut efficacement tourner pendant quelques cycles jusqu'à ce que le verrouillage soit libéré. En tournant, le thread ne se bloque pas. Ce processus est exigeant en ressources. <xref:System.Threading.SpinLock>cessera de tourner sous certaines conditions pour empêcher la privation des processeurs logiques ou l’inversion de priorité sur les systèmes avec Hyper-Threading.  
  
 Cet exemple utilise le <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> (classe), qui requiert la synchronisation utilisateur pour l’accès multithread. Dans les applications qui ciblent le .NET Framework version 4, une autre option consiste à utiliser le <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, qui ne requiert pas de tous les verrous de l’utilisateur.  
  
 Notez l’utilisation de `false` (`False` en Visual Basic) dans l’appel à <xref:System.Threading.SpinLock.Exit%2A>. Cela fournit les meilleures performances. Dans les architectures IA64, spécifiez `true` (`True`) pour utiliser la barrière mémoire, qui vide les tampons d’écriture pour garantir que le verrouillage est disponible pour la sortie des autres threads.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)
