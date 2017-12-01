---
title: Suspension et reprise des threads
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
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a>Suspension et reprise des threads
Les méthodes les plus courantes permettant de synchroniser les activités de threads consistent à bloquer et à diffuser des threads, ou à verrouiller des objets ou des régions du code. Pour plus d’informations sur ces mécanismes de verrouillage et de blocage, voir [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Vous pouvez également avoir des threads en veille. Quand des threads sont bloqués ou en veille, vous pouvez utiliser une <xref:System.Threading.ThreadInterruptedException> pour les débloquer ou les réveiller.  
  
## <a name="the-threadsleep-method"></a>La méthode Thread.Sleep  
 Appel de la <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> méthode oblige le thread actuel bloquer immédiatement pour le nombre de millisecondes ou de l’intervalle de temps que vous passez à la méthode et obtient le reste de sa tranche de temps à un autre thread. Une fois l’intervalle expiré, l’exécution du thread en veille reprend.  
  
 Un thread ne peut pas appeler <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> sur un autre thread.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>est une méthode statique qui entraîne systématiquement la mise en veille du thread actuel.  
  
 Appel de <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> avec la valeur <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> entraîne un thread en veille jusqu'à ce qu’il soit interrompu par un autre thread qui appelle la <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> méthode sur le thread en veille, ou jusqu'à ce qu’il se termine par un appel à son <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> (méthode).  L’exemple suivant illustre les deux méthodes d’interruption d’un thread en veille.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Interruption de threads  
 Vous pouvez interrompre un thread en attente en appelant le <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> méthode sur le thread bloqué pour lever une <xref:System.Threading.ThreadInterruptedException>, qui arrête le thread de l’appel bloquant. Le thread doit intercepter la <xref:System.Threading.ThreadInterruptedException> et faire tout le nécessaire pour continuer à fonctionner. Si le thread ignore l'exception, le runtime intercepte l'exception et arrête le thread.  
  
> [!NOTE]
>  Si le thread cible n'est pas bloqué quand <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> est appelé, le thread ne sera pas interrompu avant d'être bloqué. Si le thread n'est jamais bloqué, il peut se terminer sans jamais être interrompu.  
  
 En cas d'attente managée, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> réveillent le thread immédiatement. Cas d’une attente non managée (par exemple, une appel de plateforme pour Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) fonction), ni <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ni <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> peut prendre le contrôle du thread jusqu'à ce qu’il retourne vers ou appelle dans du code managé. Dans du code managé, le comportement est le suivant :  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> réveille un thread en attente et provoque la levée d'une <xref:System.Threading.ThreadInterruptedException> dans le thread de destination.  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>réveille un thread de l’attente, il est peut-être en et entraîne un <xref:System.Threading.ThreadAbortException> levée sur le thread. Pour plus d’informations, voir [Destruction de threads](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [Thread](../../../docs/standard/threading/index.md)  
 [Utilisation des threads et du threading](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
