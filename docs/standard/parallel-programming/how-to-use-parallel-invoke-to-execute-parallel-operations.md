---
title: "Comment : utiliser Parallel.Invoke pour exécuter des opérations parallèles"
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
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 942ba120fa5273f84ac3d0a51e276223de5f5484
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="b43d0-102">Comment : utiliser Parallel.Invoke pour exécuter des opérations parallèles</span><span class="sxs-lookup"><span data-stu-id="b43d0-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>
<span data-ttu-id="b43d0-103">Cet exemple indique comment paralléliser des opérations à l'aide de <xref:System.Threading.Tasks.Parallel.Invoke%2A> dans la bibliothèque parallèle de tâches.</span><span class="sxs-lookup"><span data-stu-id="b43d0-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="b43d0-104">Trois opérations sont effectuées sur la source de données partagée.</span><span class="sxs-lookup"><span data-stu-id="b43d0-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="b43d0-105">Étant donné qu'aucune des opérations ne modifie la source, elles peuvent être exécutées en parallèle de manière simple.</span><span class="sxs-lookup"><span data-stu-id="b43d0-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b43d0-106">Cette documentation utilise les expressions lambda pour définir les délégués de la bibliothèque parallèle de tâches.</span><span class="sxs-lookup"><span data-stu-id="b43d0-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="b43d0-107">Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="b43d0-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b43d0-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="b43d0-108">Example</span></span>  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 <span data-ttu-id="b43d0-109">Notez qu'avec <xref:System.Threading.Tasks.Parallel.Invoke%2A>, vous exprimez seulement quelles actions doivent s'exécuter simultanément ; le runtime gère tous les détails de planification de threads, notamment la mise à l'échelle automatique du nombre de cœurs présents sur l'ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="b43d0-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>  
  
 <span data-ttu-id="b43d0-110">Cet exemple parallélise les opérations et non les données.</span><span class="sxs-lookup"><span data-stu-id="b43d0-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="b43d0-111">Vous pouvez également paralléliser les requêtes LINQ à l'aide de PLINQ et exécuter les requêtes séquentiellement.</span><span class="sxs-lookup"><span data-stu-id="b43d0-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="b43d0-112">Vous pouvez aussi paralléliser les données à l'aide de PLINQ.</span><span class="sxs-lookup"><span data-stu-id="b43d0-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="b43d0-113">Une autre option consiste à paralléliser à la fois les requêtes et les tâches.</span><span class="sxs-lookup"><span data-stu-id="b43d0-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="b43d0-114">Bien que la surcharge résultante diminue les performances des ordinateurs hôtes avec un nombre réduit de processeurs, cela permettrait une bien meilleure mise à l'échelle des ordinateurs avec de nombreux processeurs.</span><span class="sxs-lookup"><span data-stu-id="b43d0-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b43d0-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b43d0-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b43d0-116">Copiez et collez l'exemple entier dans un projet Microsoft Visual Studio 2010 et appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="b43d0-116">Copy and paste the entire example into a Microsoft Visual Studio 2010 project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43d0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b43d0-117">See Also</span></span>  
 [<span data-ttu-id="b43d0-118">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="b43d0-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="b43d0-119">Comment : annuler une tâche et ses enfants</span><span class="sxs-lookup"><span data-stu-id="b43d0-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [<span data-ttu-id="b43d0-120">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b43d0-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
