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
# <a name="spinlock"></a><span data-ttu-id="1585e-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="1585e-102">SpinLock</span></span>
<span data-ttu-id="1585e-103">Le <xref:System.Threading.SpinLock> structure est une primitive de synchronisation de bas niveau et à exclusion mutuelle qui tourne en attendant d’acquérir un verrou.</span><span class="sxs-lookup"><span data-stu-id="1585e-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="1585e-104">Sur les ordinateurs multicœurs, lorsque les temps d’attente sont supposés être courts et que le conflit est minime, <xref:System.Threading.SpinLock> peut être plus performant que d’autres types de verrous.</span><span class="sxs-lookup"><span data-stu-id="1585e-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="1585e-105">Toutefois, nous vous recommandons d’utiliser <xref:System.Threading.SpinLock> uniquement lorsque vous déterminez par profilage que la <xref:System.Threading.Monitor?displayProperty=nameWithType> méthode ou <xref:System.Threading.Interlocked> méthodes ralentissent considérablement les performances de votre programme.</span><span class="sxs-lookup"><span data-stu-id="1585e-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="1585e-106"><xref:System.Threading.SpinLock>maîtrise la tranche horaire du thread même si elle n’a pas encore acquis le verrou.</span><span class="sxs-lookup"><span data-stu-id="1585e-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="1585e-107">Il procède ainsi pour éviter d’inversion de priorité de thread et activer le garbage collector pour rendre la progression.</span><span class="sxs-lookup"><span data-stu-id="1585e-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="1585e-108">Lorsque vous utilisez un <xref:System.Threading.SpinLock>, vérifiez qu’aucun thread ne peut contenir le verrou au-delà d’un intervalle de temps très court, et qu’aucun thread ne peut bloquer pendant qu’il détient le verrou.</span><span class="sxs-lookup"><span data-stu-id="1585e-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="1585e-109">Étant donné que le verrouillage SpinLock est un type valeur, vous devez le passer explicitement par référence si vous envisagez des deux copies pour faire référence au même verrou.</span><span class="sxs-lookup"><span data-stu-id="1585e-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="1585e-110">Pour plus d’informations sur l’utilisation de ce type, consultez <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1585e-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1585e-111">Pour obtenir un exemple, consultez [Comment : SpinLock utilisé pour la synchronisation de bas niveau](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="1585e-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="1585e-112"><xref:System.Threading.SpinLock>prend en charge un *thread*-*suivi* mode que vous pouvez utiliser pendant la phase de développement pour aider à suivre le thread qui détient le verrou à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="1585e-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="1585e-113">Mode de suivi des threads est très utile pour le débogage, mais nous recommandons que vous désactivez cette option dans la version release de votre programme, car elle peut ralentir les performances.</span><span class="sxs-lookup"><span data-stu-id="1585e-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="1585e-114">Pour plus d’informations, consultez [Comment : Mode de suivi permettent de threads dans le verrouillage SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span><span class="sxs-lookup"><span data-stu-id="1585e-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1585e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1585e-115">See Also</span></span>  
 [<span data-ttu-id="1585e-116">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="1585e-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
