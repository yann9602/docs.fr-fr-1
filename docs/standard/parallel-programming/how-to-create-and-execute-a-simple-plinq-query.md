---
title: "Comment : créer et exécuter une requête PLINQ simple"
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
helpviewer_keywords: PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a99eedc05bbf8d4dcd58e46b484bd57c29f70886
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="c0635-102">Comment : créer et exécuter une requête PLINQ simple</span><span class="sxs-lookup"><span data-stu-id="c0635-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="c0635-103">L'exemple suivant montre comment créer une requête Parallel LINQ simple à l'aide de la méthode d'extension <xref:System.Linq.ParallelEnumerable.AsParallel%2A> sur la séquence source, et exécuter la requête à l'aide de la méthode <xref:System.Linq.ParallelEnumerable.ForAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0635-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0635-104">Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c0635-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="c0635-105">Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="c0635-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0635-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0635-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="c0635-107">Cet exemple montre le modèle de base pour la création et l’exécution d’une requête Parallel LINQ quand le classement de la séquence de résultat n’est pas important ; les requêtes non classées sont généralement plus rapides que les requêtes classées.</span><span class="sxs-lookup"><span data-stu-id="c0635-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="c0635-108">La requête partitionne la source en tâches qui sont exécutées de façon asynchrone sur plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="c0635-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="c0635-109">L'ordre dans lequel chaque tâche se termine ne dépend pas uniquement de la quantité de travail impliquée pour traiter les éléments de la partition, mais également de facteurs externes tels que la façon dont le système d'exploitation planifie chaque thread.</span><span class="sxs-lookup"><span data-stu-id="c0635-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="c0635-110">Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.</span><span class="sxs-lookup"><span data-stu-id="c0635-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c0635-111">Pour plus d’informations sur l’accélération, consultez [fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c0635-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="c0635-112">Pour plus d’informations sur la façon de conserver l’ordre des éléments dans une requête, consultez [Comment : contrôle de tri dans une requête PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="c0635-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0635-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0635-113">See Also</span></span>  
 [<span data-ttu-id="c0635-114">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c0635-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
