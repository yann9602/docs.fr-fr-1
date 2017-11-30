---
title: Verrous de lecteur-writer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df06e83165906199774f99de4140ace9b7396cbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="reader-writer-locks"></a><span data-ttu-id="2384e-102">Verrous de lecteur-writer</span><span class="sxs-lookup"><span data-stu-id="2384e-102">Reader-Writer Locks</span></span>
<span data-ttu-id="2384e-103">La <xref:System.Threading.ReaderWriterLockSlim> classe permet à plusieurs threads de lire une ressource simultanément, mais nécessite qu’un thread d’attendre un verrou exclusif afin d’écrire dans la ressource.</span><span class="sxs-lookup"><span data-stu-id="2384e-103">The <xref:System.Threading.ReaderWriterLockSlim> class enables multiple threads to read a resource concurrently, but requires a thread to wait for an exclusive lock in order to write to the resource.</span></span>  
  
 <span data-ttu-id="2384e-104">Vous pouvez utiliser un <xref:System.Threading.ReaderWriterLockSlim> dans votre application pour fournir une synchronisation coopérative parmi les threads qui accèdent à une ressource partagée.</span><span class="sxs-lookup"><span data-stu-id="2384e-104">You might use a <xref:System.Threading.ReaderWriterLockSlim> in your application to provide cooperative synchronization among threads that access a shared resource.</span></span> <span data-ttu-id="2384e-105">Les verrous sont effectuées sur le <xref:System.Threading.ReaderWriterLockSlim> lui-même.</span><span class="sxs-lookup"><span data-stu-id="2384e-105">Locks are taken on the <xref:System.Threading.ReaderWriterLockSlim> itself.</span></span>  
  
 <span data-ttu-id="2384e-106">Comme avec tout mécanisme de synchronisation de threads, vous devez vous assurer qu’aucun thread ignore le verrouillage fourni par <xref:System.Threading.ReaderWriterLockSlim>.</span><span class="sxs-lookup"><span data-stu-id="2384e-106">As with any thread synchronization mechanism, you must ensure that no threads bypass the locking that is provided by <xref:System.Threading.ReaderWriterLockSlim>.</span></span> <span data-ttu-id="2384e-107">Un pour s’en assurer consiste à concevoir une classe qui encapsule la ressource partagée.</span><span class="sxs-lookup"><span data-stu-id="2384e-107">One way to ensure this is to design a class that encapsulates the shared resource.</span></span> <span data-ttu-id="2384e-108">Cette classe fournirait des membres qui accèdent à la ressource partagée privée et qui utilisent une privée <xref:System.Threading.ReaderWriterLockSlim> pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="2384e-108">This class would provide members that access the private shared resource and that use a private <xref:System.Threading.ReaderWriterLockSlim> for synchronization.</span></span> <span data-ttu-id="2384e-109">Pour obtenir un exemple, consultez l’exemple de code pour la <xref:System.Threading.ReaderWriterLockSlim> classe.</span><span class="sxs-lookup"><span data-stu-id="2384e-109">For an example, see the code example for the <xref:System.Threading.ReaderWriterLockSlim> class.</span></span> <span data-ttu-id="2384e-110"><xref:System.Threading.ReaderWriterLockSlim>est suffisamment efficace pour être utilisé pour synchroniser des objets individuels.</span><span class="sxs-lookup"><span data-stu-id="2384e-110"><xref:System.Threading.ReaderWriterLockSlim> is efficient enough to be used to synchronize individual objects.</span></span>  
  
 <span data-ttu-id="2384e-111">Structurer votre application pour réduire la durée de lecture et d’opérations d’écriture.</span><span class="sxs-lookup"><span data-stu-id="2384e-111">Structure your application to minimize the duration of read and write operations.</span></span> <span data-ttu-id="2384e-112">Longues opérations d’écriture affectent le débit directement car le verrou en écriture est exclusif.</span><span class="sxs-lookup"><span data-stu-id="2384e-112">Long write operations affect throughput directly because the write lock is exclusive.</span></span> <span data-ttu-id="2384e-113">Long writers en attente de bloquer les opérations de lecture, et si au moins un thread est en attente pour un accès en écriture, les threads qui demandent l’accès en lecture seront également bloqués.</span><span class="sxs-lookup"><span data-stu-id="2384e-113">Long read operations block waiting writers, and if at least one thread is waiting for write access, threads that request read access will be blocked as well.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2384e-114">Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] a deux verrous de lecteur-writer, <xref:System.Threading.ReaderWriterLockSlim> et <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="2384e-114">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] has two reader-writer locks, <xref:System.Threading.ReaderWriterLockSlim> and <xref:System.Threading.ReaderWriterLock>.</span></span> <span data-ttu-id="2384e-115"><xref:System.Threading.ReaderWriterLockSlim>est recommandée pour tout nouveau développement.</span><span class="sxs-lookup"><span data-stu-id="2384e-115"><xref:System.Threading.ReaderWriterLockSlim> is recommended for all new development.</span></span> <span data-ttu-id="2384e-116"><xref:System.Threading.ReaderWriterLockSlim>est semblable à <xref:System.Threading.ReaderWriterLock>, mais les règles de récurrence et de mise à niveau et la rétrogradation de l’état de verrou sont simplifiées.</span><span class="sxs-lookup"><span data-stu-id="2384e-116"><xref:System.Threading.ReaderWriterLockSlim> is similar to <xref:System.Threading.ReaderWriterLock>, but it has simplified rules for recursion and for upgrading and downgrading lock state.</span></span> <span data-ttu-id="2384e-117"><xref:System.Threading.ReaderWriterLockSlim>évite de nombreux cas d’interblocage potentiel.</span><span class="sxs-lookup"><span data-stu-id="2384e-117"><xref:System.Threading.ReaderWriterLockSlim> avoids many cases of potential deadlock.</span></span> <span data-ttu-id="2384e-118">En outre, les performances de <xref:System.Threading.ReaderWriterLockSlim> est considérablement plus performants que <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="2384e-118">In addition, the performance of <xref:System.Threading.ReaderWriterLockSlim> is significantly better than <xref:System.Threading.ReaderWriterLock>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2384e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2384e-119">See Also</span></span>  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [<span data-ttu-id="2384e-120">Thread</span><span class="sxs-lookup"><span data-stu-id="2384e-120">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="2384e-121">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="2384e-121">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
