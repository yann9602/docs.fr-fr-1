---
title: "Comment : annuler une boucle Parallel.For ou ForEach"
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
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="bdfe2-102">Comment : annuler une boucle Parallel.For ou ForEach</span><span class="sxs-lookup"><span data-stu-id="bdfe2-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="bdfe2-103">Le <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> méthodes prennent en charge l’annulation via l’utilisation de jetons d’annulation.</span><span class="sxs-lookup"><span data-stu-id="bdfe2-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="bdfe2-104">Pour plus d’informations sur l’annulation en général, consultez [annulation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="bdfe2-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="bdfe2-105">Dans une boucle parallèle, vous fournissez le <xref:System.Threading.CancellationToken> à la méthode dans le <xref:System.Threading.Tasks.ParallelOptions> paramètre et puis joignez l’appel parallèle dans un bloc try-catch.</span><span class="sxs-lookup"><span data-stu-id="bdfe2-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdfe2-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="bdfe2-106">Example</span></span>  
 <span data-ttu-id="bdfe2-107">L’exemple suivant montre comment annuler un appel à <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bdfe2-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bdfe2-108">Vous pouvez appliquer la même approche pour un <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> appeler.</span><span class="sxs-lookup"><span data-stu-id="bdfe2-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="bdfe2-109">Si le jeton qui signale l’annulation est le même jeton qui est spécifié dans le <xref:System.Threading.Tasks.ParallelOptions> de l’instance, puis la boucle parallèle lèvera une seule <xref:System.OperationCanceledException> d’annulation.</span><span class="sxs-lookup"><span data-stu-id="bdfe2-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="bdfe2-110">Si un autre jeton provoque l’annulation, la boucle lèvera une <xref:System.AggregateException> avec un <xref:System.OperationCanceledException> comme InnerException.</span><span class="sxs-lookup"><span data-stu-id="bdfe2-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfe2-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdfe2-111">See Also</span></span>  
 [<span data-ttu-id="bdfe2-112">Parallélisme de données</span><span class="sxs-lookup"><span data-stu-id="bdfe2-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="bdfe2-113">Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="bdfe2-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
