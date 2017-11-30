---
title: "Comment : spécifier des options de fusion en PLINQ"
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
helpviewer_keywords: PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec601e8bbefd31650fb91c438b032942cfc93101
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="29c03-102">Comment : spécifier des options de fusion en PLINQ</span><span class="sxs-lookup"><span data-stu-id="29c03-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="29c03-103">Cet exemple montre comment spécifier les options de fusion qui seront appliquent à tous les opérateurs suivants dans une requête PLINQ.</span><span class="sxs-lookup"><span data-stu-id="29c03-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="29c03-104">Il est inutile de définir explicitement les options de fusion, mais cela peut améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="29c03-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="29c03-105">Pour plus d’informations sur les options de fusion, consultez [les Options de fusion en PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="29c03-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="29c03-106">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="29c03-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="29c03-107">Pour plus d’informations sur l’accélération, consultez [fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="29c03-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29c03-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="29c03-108">Example</span></span>  
 <span data-ttu-id="29c03-109">L’exemple suivant illustre le comportement des options de fusion dans un scénario de base qui a une source non ordonnée et s’applique une fonction coûteuse à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="29c03-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="29c03-110">Dans le cas où la <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option entraîne une latence indésirable avant le premier élément est transmis, essayez du <xref:System.Linq.ParallelMergeOptions.NotBuffered> option pour générer des éléments de résultat plus rapidement et plus facilement.</span><span class="sxs-lookup"><span data-stu-id="29c03-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c03-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29c03-111">See Also</span></span>  
 <xref:System.Linq.ParallelMergeOptions>  
 [<span data-ttu-id="29c03-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="29c03-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
