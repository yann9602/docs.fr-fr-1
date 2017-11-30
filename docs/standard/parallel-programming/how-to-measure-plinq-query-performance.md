---
title: "Comment : mesurer les performances de requêtes PLINQ"
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
helpviewer_keywords: PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03432e70454cb6203e55e340111a6cb7efe62dc4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="bd751-102">Comment : mesurer les performances de requêtes PLINQ</span><span class="sxs-lookup"><span data-stu-id="bd751-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="bd751-103">Cet exemple montre comment utiliser la <xref:System.Diagnostics.Stopwatch> classe pour mesurer le temps nécessaire pour exécuter une requête PLINQ.</span><span class="sxs-lookup"><span data-stu-id="bd751-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd751-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd751-104">Example</span></span>  
 <span data-ttu-id="bd751-105">Cet exemple utilise une boucle `foreach` vide (`For Each` en Visual Basic) pour mesurer le temps nécessaire à l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="bd751-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="bd751-106">Dans le code réel, la boucle contient généralement des étapes de traitement supplémentaires qui s’ajoutent à la durée d’exécution totale de la requête.</span><span class="sxs-lookup"><span data-stu-id="bd751-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="bd751-107">Notez que le chronomètre est démarré juste avant la boucle qui marque le début d’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="bd751-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="bd751-108">Si vous avez besoin de mesures plus poussées, vous pouvez utiliser la propriété `ElapsedTicks` au lieu de `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="bd751-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="bd751-109">La durée d’exécution totale est une mesure utile lorsque vous expérimentez des implémentations de requête, même si elle ne donne pas toujours tous les détails.</span><span class="sxs-lookup"><span data-stu-id="bd751-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="bd751-110">Utilisez le visualiseur concurrentiel pour avoir une vision plus approfondie et plus riche de l’interaction des threads de requête entre eux et avec d’autres processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bd751-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="bd751-111">Pour plus d’informations, consultez [Visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="bd751-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd751-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd751-112">See Also</span></span>  
 [<span data-ttu-id="bd751-113">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="bd751-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
