---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a>SpinLock
Le <xref:System.Threading.SpinLock> structure est une primitive de synchronisation de bas niveau et à exclusion mutuelle qui tourne en attendant d’acquérir un verrou. Sur les ordinateurs multicœurs, lorsque les temps d’attente sont supposés être courts et que le conflit est minime, <xref:System.Threading.SpinLock> peut être plus performant que d’autres types de verrous. Toutefois, nous vous recommandons d’utiliser <xref:System.Threading.SpinLock> uniquement lorsque vous déterminez par profilage que la <xref:System.Threading.Monitor?displayProperty=nameWithType> méthode ou <xref:System.Threading.Interlocked> méthodes ralentissent considérablement les performances de votre programme.  
  
 <xref:System.Threading.SpinLock>maîtrise la tranche horaire du thread même si elle n’a pas encore acquis le verrou. Il procède ainsi pour éviter d’inversion de priorité de thread et activer le garbage collector pour rendre la progression. Lorsque vous utilisez un <xref:System.Threading.SpinLock>, vérifiez qu’aucun thread ne peut contenir le verrou au-delà d’un intervalle de temps très court, et qu’aucun thread ne peut bloquer pendant qu’il détient le verrou.  
  
 Étant donné que le verrouillage SpinLock est un type valeur, vous devez le passer explicitement par référence si vous envisagez des deux copies pour faire référence au même verrou.  
  
 Pour plus d’informations sur l’utilisation de ce type, consultez <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Pour obtenir un exemple, consultez [Comment : SpinLock utilisé pour la synchronisation de bas niveau](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>prend en charge un *thread*-*suivi* mode que vous pouvez utiliser pendant la phase de développement pour aider à suivre le thread qui détient le verrou à un moment donné. Mode de suivi des threads est très utile pour le débogage, mais nous recommandons que vous désactivez cette option dans la version release de votre programme, car elle peut ralentir les performances. Pour plus d’informations, consultez [Comment : Mode de suivi permettent de threads dans le verrouillage SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)
