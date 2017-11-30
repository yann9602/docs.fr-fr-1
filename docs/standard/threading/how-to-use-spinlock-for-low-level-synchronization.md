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
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="8d8d0-102">Comment : utiliser le verrouillage spinlock pour une synchronisation de bas niveau</span><span class="sxs-lookup"><span data-stu-id="8d8d0-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="8d8d0-103">L’exemple suivant montre comment utiliser un <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d8d0-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d8d0-104">Example</span></span>  
 <span data-ttu-id="8d8d0-105">Dans cet exemple, la section critique exécute une quantité minimale de travail, ce qui en fait un bon candidat pour un <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="8d8d0-106">Le travail une petite quantité d’augmenter les performances de la <xref:System.Threading.SpinLock> par rapport à un verrou standard.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="8d8d0-107">Toutefois, à un moment, le verrouillage tournant devient plus coûteux qu’un verrouillage standard.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="8d8d0-108">Vous pouvez utiliser la fonctionnalité de profilage d'accès concurrentiel dans les outils de profilage pour voir quel type de verrouillage offre les meilleures performances pour votre programme.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="8d8d0-109">Pour plus d’informations, consultez [Visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="8d8d0-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="8d8d0-110"><xref:System.Threading.SpinLock>peut être utile lorsqu’un verrou sur une ressource partagée ne va pas être maintenu pendant très long.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="8d8d0-111">Dans ce cas, sur les ordinateurs multicœurs, le thread bloqué peut efficacement tourner pendant quelques cycles jusqu'à ce que le verrouillage soit libéré.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="8d8d0-112">En tournant, le thread ne se bloque pas. Ce processus est exigeant en ressources.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="8d8d0-113"><xref:System.Threading.SpinLock>cessera de tourner sous certaines conditions pour empêcher la privation des processeurs logiques ou l’inversion de priorité sur les systèmes avec Hyper-Threading.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="8d8d0-114">Cet exemple utilise le <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> (classe), qui requiert la synchronisation utilisateur pour l’accès multithread.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="8d8d0-115">Dans les applications qui ciblent le .NET Framework version 4, une autre option consiste à utiliser le <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, qui ne requiert pas de tous les verrous de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="8d8d0-116">Notez l’utilisation de `false` (`False` en Visual Basic) dans l’appel à <xref:System.Threading.SpinLock.Exit%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="8d8d0-117">Cela fournit les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-117">This provides the best performance.</span></span> <span data-ttu-id="8d8d0-118">Dans les architectures IA64, spécifiez `true` (`True`) pour utiliser la barrière mémoire, qui vide les tampons d’écriture pour garantir que le verrouillage est disponible pour la sortie des autres threads.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8d0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d8d0-119">See Also</span></span>  
 [<span data-ttu-id="8d8d0-120">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="8d8d0-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
