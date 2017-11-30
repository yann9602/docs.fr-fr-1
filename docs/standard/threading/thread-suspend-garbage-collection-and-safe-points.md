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
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="8e2d7-102">Thread.Suspend, Garbage Collection et les points sans risque</span><span class="sxs-lookup"><span data-stu-id="8e2d7-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="8e2d7-103">Lorsque vous appelez <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> sur un thread, le système indique qu’une suspension du thread a été demandée et permet au thread d’exécution jusqu'à ce qu’il a atteint un point sans risque avant d’interrompre le thread.</span><span class="sxs-lookup"><span data-stu-id="8e2d7-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="8e2d7-104">Un point sans risque pour un thread est un point dans son exécution à laquelle les garbage collection peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="8e2d7-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="8e2d7-105">Une fois qu’un point sans risque est atteinte, le runtime garantit que le thread suspendu ne sera pas avancer dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="8e2d7-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="8e2d7-106">Un thread d’exécution en dehors du code managé est toujours sécurisé pour le garbage collection, et son exécution se poursuit jusqu'à ce qu’il tente de reprendre l’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="8e2d7-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e2d7-107">Pour effectuer un garbage collection, le runtime doit suspendre tous les threads sauf le thread qui effectue la collection.</span><span class="sxs-lookup"><span data-stu-id="8e2d7-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="8e2d7-108">Chaque thread doit être acheminé vers un point sans risque avant de pouvoir être suspendu.</span><span class="sxs-lookup"><span data-stu-id="8e2d7-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e2d7-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e2d7-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="8e2d7-110">Thread</span><span class="sxs-lookup"><span data-stu-id="8e2d7-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="8e2d7-111">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="8e2d7-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
