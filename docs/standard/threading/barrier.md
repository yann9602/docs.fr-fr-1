---
title: "Cloisonnement (.NET Framework)"
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
helpviewer_keywords: synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a8111cc9f2798ff96be8b128f22a75d21b441178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="barrier-net-framework"></a><span data-ttu-id="cc408-102">Cloisonnement (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="cc408-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="cc408-103">A *barrière* est une défini par l’utilisateur primitive de synchronisation qui permet à plusieurs threads (appelés *participants*) de travailler simultanément sur un algorithme en plusieurs phases.</span><span class="sxs-lookup"><span data-stu-id="cc408-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="cc408-104">Chaque participant s'exécute jusqu'à ce qu'il atteigne le point de cloisonnement dans le code.</span><span class="sxs-lookup"><span data-stu-id="cc408-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="cc408-105">Le cloisonnement représente la fin d'une phase de travail.</span><span class="sxs-lookup"><span data-stu-id="cc408-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="cc408-106">Quand un participant atteint le cloisonnement, il se bloque jusqu'à ce que tous les participants aient atteint le même cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="cc408-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="cc408-107">Une fois que tous les participants ont atteint le cloisonnement, vous pouvez éventuellement appeler une action post-phase.</span><span class="sxs-lookup"><span data-stu-id="cc408-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="cc408-108">Cette action post-phase peut être utilisée pour effectuer des actions avec un thread unique alors que tous les autres threads sont encore bloqués.</span><span class="sxs-lookup"><span data-stu-id="cc408-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="cc408-109">Une fois l'action exécutée, tous les participants sont débloqués.</span><span class="sxs-lookup"><span data-stu-id="cc408-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="cc408-110">L’extrait de code suivant montre un modèle de cloisonnement de base.</span><span class="sxs-lookup"><span data-stu-id="cc408-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="cc408-111">Pour obtenir un exemple complet, consultez [Comment : synchroniser des opérations simultanées avec un objet Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="cc408-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="cc408-112">Ajout et suppression des participants</span><span class="sxs-lookup"><span data-stu-id="cc408-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="cc408-113">Quand vous créez un <xref:System.Threading.Barrier>, spécifiez le nombre de participants.</span><span class="sxs-lookup"><span data-stu-id="cc408-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="cc408-114">Vous pouvez également ajouter ou supprimer des participants dynamiquement à tout moment.</span><span class="sxs-lookup"><span data-stu-id="cc408-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="cc408-115">Par exemple, si un participant résout sa partie du problème, vous pouvez stocker le résultat, arrêter l’exécution sur ce thread et appeler <xref:System.Threading.Barrier.RemoveParticipant%2A> pour décrémenter le nombre de participants du cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="cc408-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="cc408-116">Quand vous ajoutez un participant en appelant <xref:System.Threading.Barrier.AddParticipant%2A>, la valeur de retour spécifie le numéro de la phase actuelle, ce qui peut être utile pour initialiser le travail du nouveau participant.</span><span class="sxs-lookup"><span data-stu-id="cc408-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="cc408-117">Cloisonnements cassés</span><span class="sxs-lookup"><span data-stu-id="cc408-117">Broken Barriers</span></span>  
 <span data-ttu-id="cc408-118">Des blocages peuvent se produire si un participant ne parvient pas à atteindre le cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="cc408-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="cc408-119">Pour éviter ces blocages, utilisez les surcharges de la méthode <xref:System.Threading.Barrier.SignalAndWait%2A> pour spécifier un délai d'attente et un jeton d'annulation.</span><span class="sxs-lookup"><span data-stu-id="cc408-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="cc408-120">Ces surcharges retournent une valeur booléenne que chaque participant peut vérifier avant de passer à la phase suivante.</span><span class="sxs-lookup"><span data-stu-id="cc408-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="cc408-121">Exceptions post-phase</span><span class="sxs-lookup"><span data-stu-id="cc408-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="cc408-122">Si le délégué post-phase lève une exception, il est encapsulé dans un objet <xref:System.Threading.BarrierPostPhaseException> qui est ensuite propagé à tous les participants.</span><span class="sxs-lookup"><span data-stu-id="cc408-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="cc408-123">Cloisonnement et ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="cc408-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="cc408-124">Les cloisonnements sont particulièrement utiles quand les threads exécutent plusieurs phases dans des boucles.</span><span class="sxs-lookup"><span data-stu-id="cc408-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="cc408-125">Si votre code requiert uniquement une ou deux phases de travail, songez à utiliser des objets <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> avec n'importe quel type de jointure implicite, notamment :</span><span class="sxs-lookup"><span data-stu-id="cc408-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="cc408-126">Pour plus d’informations, consultez [Chaînage des tâches à l’aide de tâches de continuation](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="cc408-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc408-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc408-127">See Also</span></span>  
 [<span data-ttu-id="cc408-128">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="cc408-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="cc408-129">Guide pratique pour synchroniser des opérations simultanées avec un objet Barrier</span><span class="sxs-lookup"><span data-stu-id="cc408-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
