---
title: "Comment : activer le mode de suivi des threads dans le verrouillage Spinlock"
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
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Comment : activer le mode de suivi des threads dans le verrouillage Spinlock
<xref:System.Threading.SpinLock?displayProperty=nameWithType>est un verrou d’exclusion mutuelle de bas niveau que vous pouvez utiliser pour les scénarios qui ont des durées d’attente très courtes. <xref:System.Threading.SpinLock>n’est pas réentrant. Après qu’un thread entré le verrou, il doit quitter correctement avant de pouvoir à nouveau entrer. En règle générale, toute tentative d’entrer à nouveau le verrou provoquerait un interblocage et les interblocages peuvent être très difficiles à déboguer. Comme une aide au développement, <xref:System.Threading.SpinLock?displayProperty=nameWithType> prend en charge un mode de suivi de thread qui lève une exception levée lorsqu’un thread tente de réentrer un verrou qu’il détient déjà. Cela vous permet de que retrouver plus facilement le point auquel le verrou a été pas fermé correctement. Vous pouvez activer le mode de suivi de thread à l’aide de la <xref:System.Threading.SpinLock> constructeur qui accepte une valeur booléenne d’entrée et en passant un argument de `true`. Après avoir terminé le développement et les phases de test, désactivez le mode de suivi des threads pour optimiser les performances.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le mode de suivi de thread. Les lignes de quitter correctement le verrou sont commentées pour simuler une erreur de codage provoquant l’un des résultats suivants :  
  
-   Une exception est levée si le <xref:System.Threading.SpinLock> a été créé à l’aide d’un argument de `true` (`True` en Visual Basic).  
  
-   Interblocage si le <xref:System.Threading.SpinLock> a été créé à l’aide d’un argument de `false` (`False` en Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Voir aussi  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
