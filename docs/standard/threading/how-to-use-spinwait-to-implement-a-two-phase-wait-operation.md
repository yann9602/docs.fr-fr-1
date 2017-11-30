---
title: "Comment : utiliser SpinWait pour implémenter une opération d'attente en deux phases"
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
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Comment : utiliser SpinWait pour implémenter une opération d'attente en deux phases
L’exemple suivant montre comment utiliser un <xref:System.Threading.SpinWait?displayProperty=nameWithType> objet pour implémenter une opération d’attente en deux phases. Dans la première phase, l’objet de synchronisation, un `Latch`, tourne pendant quelques cycles pendant qu’il vérifie si le verrou est devenu disponible. Dans la deuxième phase, si le verrou devienne disponible, le `Wait` méthode est retournée sans utiliser le <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> à exécuter son attente ; sinon, `Wait` exécute l’attente.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre une implémentation de base d’une synchronisation de verrou primitive. Vous pouvez utiliser cette structure de données lorsque le temps d’attente sont supposés être très courts. Cet exemple est uniquement à des fins de démonstration. Si vous avez besoin des fonctionnalités de type de verrou dans votre programme, envisagez d’utiliser <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Le verrou utilise le <xref:System.Threading.SpinWait> objet à mettre en place uniquement jusqu’au prochain appel à `SpinOnce` provoque le <xref:System.Threading.SpinWait> à générer la tranche horaire du thread. À ce stade, le verrou provoque son propre changement de contexte en appelant <xref:System.Threading.WaitHandle.WaitOne%2A> sur la <xref:System.Threading.ManualResetEvent> et en passant le reste de la valeur de délai d’attente.  
  
 La sortie d’enregistrement indique la fréquence à laquelle le verrou n’a pu augmenter les performances en acquérir le verrou sans utiliser le <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Voir aussi  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)
