---
title: "Comment : synchroniser des opérations simultanées avec un objet Barrier"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="d5380-102">Comment : synchroniser des opérations simultanées avec un objet Barrier</span><span class="sxs-lookup"><span data-stu-id="d5380-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="d5380-103">L’exemple suivant montre comment synchroniser des tâches simultanées avec un <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="d5380-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5380-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5380-104">Example</span></span>  
 <span data-ttu-id="d5380-105">L’objectif du programme suivant est pour compter le nombre itérations (ou phases) sont requis pour deux threads trouvent leur moitié de la solution sur la même phase à l’aide d’un algorithme aléatoire remanier les mots.</span><span class="sxs-lookup"><span data-stu-id="d5380-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="d5380-106">Une fois que chaque thread a mélangé ses mots, l’opération post-phase de cloisonnement compare les deux résultats pour voir si la phrase complète a été restituée dans l’ordre correct des mots.</span><span class="sxs-lookup"><span data-stu-id="d5380-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="d5380-107">A <xref:System.Threading.Barrier> est un objet qui empêche des tâches individuelles dans une opération parallèle de se poursuivre jusqu'à ce que toutes les tâches atteignent le cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="d5380-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="d5380-108">Il est utile lorsqu’une opération parallèle se produit en plusieurs phases, et chaque phase requiert la synchronisation entre les tâches.</span><span class="sxs-lookup"><span data-stu-id="d5380-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="d5380-109">Dans cet exemple, il existe deux phases à l’opération.</span><span class="sxs-lookup"><span data-stu-id="d5380-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="d5380-110">Dans la première phase, chaque tâche remplit sa section de la mémoire tampon avec des données.</span><span class="sxs-lookup"><span data-stu-id="d5380-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="d5380-111">Lors de chaque tâche a rempli sa section, la tâche signale le cloisonnement qu’il est prêt à continuer, puis attend.</span><span class="sxs-lookup"><span data-stu-id="d5380-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="d5380-112">Lorsque toutes les tâches ont signalé le cloisonnement, elles sont débloqués et la deuxième phase démarre.</span><span class="sxs-lookup"><span data-stu-id="d5380-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="d5380-113">Le cloisonnement est nécessaire car la deuxième phase requiert que chaque tâche ait accès à toutes les données qui a été généré pour ce point.</span><span class="sxs-lookup"><span data-stu-id="d5380-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="d5380-114">Sans le cloisonnement, les premières tâches à effectuer peuvent tenter de lire à partir de mémoires tampons qui les n'ont pas encore été remplies par d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="d5380-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="d5380-115">Vous pouvez synchroniser n’importe quel nombre de phases de cette manière.</span><span class="sxs-lookup"><span data-stu-id="d5380-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5380-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5380-116">See Also</span></span>  
 [<span data-ttu-id="d5380-117">Structures de données pour la programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="d5380-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
