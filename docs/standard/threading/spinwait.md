---
title: SpinWait
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
helpviewer_keywords: synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfaf85c0fe1de3be89618ae540e9c183b66a11eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>est un type de synchronisation légers que vous pouvez utiliser dans les scénarios de bas niveau pour éviter les changements de contexte et les transitions de noyau qui sont requises pour les événements de noyau. Sur les ordinateurs multicœurs, lorsqu’une ressource n’est pas censée être maintenus pendant de longues périodes de temps, il peut être plus efficace pour un thread en attente à tourner en mode utilisateur pendant quelques douzaines ou centaines de cycles, puis de réessayer d’acquérir la ressource. Si la ressource est disponible après rotation, vous avez enregistré plusieurs milliers de cycles. Si la ressource est toujours pas disponible, vous avez passé à uniquement quelques cycles et pouvez toujours entrer une attente basée sur le noyau. Cette combinaison de rotation, puis attente est parfois appelée une *une opération d’attente en deux phases*.  
  
 <xref:System.Threading.SpinWait>est conçu pour être utilisé conjointement avec les types .NET Framework qui encapsulent les événements de noyau tels que <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait>peut également être utilisé par lui-même pour la fonctionnalité de rotation de base dans un seul programme.  
  
 <xref:System.Threading.SpinWait>est plus qu’une boucle vide. Il est implémenté avec soin pour fournir le comportement de rotation correct pour les cas généraux et initialise lui-même des changements de contexte s’il tourne assez longtemps (à peu près la longueur de la durée nécessaire à une transition de noyau). Par exemple, sur les ordinateurs à cœur unique, <xref:System.Threading.SpinWait> produit la tranche horaire du thread immédiatement, car la rotation bloque la progression sur tous les threads. <xref:System.Threading.SpinWait>génère même sur les ordinateurs multicœurs pour empêcher le blocage des threads de priorité plus élevée ou le garbage collector du thread en attente. Par conséquent, si vous utilisez un <xref:System.Threading.SpinWait> dans une opération d’attente en deux phases, nous vous recommandons d’appeler l’attente de noyau avant le <xref:System.Threading.SpinWait> lui-même initie un changement de contexte. <xref:System.Threading.SpinWait>Fournit la <xref:System.Threading.SpinWait.NextSpinWillYield%2A> propriété que vous pouvez vérifier avant chaque appel à <xref:System.Threading.SpinWait.SpinOnce%2A>. Lorsque la propriété retourne `true`, initialisez votre propre opération d’attente. Pour obtenir un exemple, consultez [Comment : utiliser des SpinWait pour implémenter une opération d’attente à deux phases](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Si vous n’effectuez pas une opération d’attente en deux phases, mais fonctionnent uniquement jusqu'à ce qu’une condition soit remplie, vous pouvez activer <xref:System.Threading.SpinWait> pour effectuer son contexte bascule afin qu’il soit un bon citoyen dans l’environnement de système d’exploitation Windows. L’exemple de base suivant montre un <xref:System.Threading.SpinWait> dans une pile sans verrou. Si vous avez besoin d’une pile de hautes performances, thread-safe, envisagez d’utiliser <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)
