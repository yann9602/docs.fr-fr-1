---
title: Thread.Suspend, Garbage Collection et les points sans risque
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend, Garbage Collection et les points sans risque
Lorsque vous appelez <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> sur un thread, le système indique qu’une suspension du thread a été demandée et permet au thread d’exécution jusqu'à ce qu’il a atteint un point sans risque avant d’interrompre le thread. Un point sans risque pour un thread est un point dans son exécution à laquelle les garbage collection peut être exécuté.  
  
 Une fois qu’un point sans risque est atteinte, le runtime garantit que le thread suspendu ne sera pas avancer dans le code managé. Un thread d’exécution en dehors du code managé est toujours sécurisé pour le garbage collection, et son exécution se poursuit jusqu'à ce qu’il tente de reprendre l’exécution du code managé.  
  
> [!NOTE]
>  Pour effectuer un garbage collection, le runtime doit suspendre tous les threads sauf le thread qui effectue la collection. Chaque thread doit être acheminé vers un point sans risque avant de pouvoir être suspendu.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [Thread](../../../docs/standard/threading/index.md)  
 [Gestion automatique de la mémoire](../../../docs/standard/automatic-memory-management.md)
