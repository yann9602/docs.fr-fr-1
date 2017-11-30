---
title: "Comment : combiner des requêtes LINQ parallèles et séquentielles"
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
helpviewer_keywords: parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4da91ff535059b181baa637164a854cd75d06334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="b55e2-102">Comment : combiner des requêtes LINQ parallèles et séquentielles</span><span class="sxs-lookup"><span data-stu-id="b55e2-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="b55e2-103">Cet exemple montre comment utiliser la <xref:System.Linq.ParallelEnumerable.AsSequential%2A> méthode pour indiquer à PLINQ de traiter de manière séquentielle tous les opérateurs suivants dans la requête.</span><span class="sxs-lookup"><span data-stu-id="b55e2-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="b55e2-104">Bien que le traitement séquentiel est généralement plus lent que parallèle, il est parfois nécessaire pour produire des résultats corrects.</span><span class="sxs-lookup"><span data-stu-id="b55e2-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b55e2-105">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="b55e2-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="b55e2-106">Pour plus d’informations sur l’accélération, consultez [fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="b55e2-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b55e2-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="b55e2-107">Example</span></span>  
 <span data-ttu-id="b55e2-108">L’exemple suivant montre un scénario dans lequel <xref:System.Linq.ParallelEnumerable.AsSequential%2A> est obligatoire, pour conserver le classement qui a été établie dans une clause précédente de la requête.</span><span class="sxs-lookup"><span data-stu-id="b55e2-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b55e2-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b55e2-109">Compiling the Code</span></span>  
 <span data-ttu-id="b55e2-110">Pour compiler et exécuter ce code, collez-le dans le [données PLINQ, exemple](../../../docs/standard/parallel-programming/plinq-data-sample.md) de projet, ajoutez une ligne pour appeler la méthode à partir de `Main`, et appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="b55e2-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b55e2-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b55e2-111">See Also</span></span>  
 [<span data-ttu-id="b55e2-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b55e2-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
