---
title: "Comment : spécifier le mode d'exécution en PLINQ"
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
helpviewer_keywords: PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 745ceae9832582c7b66a56075d128f9cf1c8ff69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Comment : spécifier le mode d'exécution en PLINQ
Cet exemple montre comment forcer PLINQ à ignorer son approche par défaut et paralléliser une requête, quelle que soit la forme de la requête.  
  
> [!WARNING]
>  Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ est conçu pour exploiter les possibilités de parallélisation. Toutefois, toutes les requêtes bénéficient de l’exécution en parallèle. Par exemple, lorsqu’une requête contient un délégué d’utilisateur unique qui est très peu de travail, la requête sera exécutée généralement plus rapide de manière séquentielle. Il s’agit, car l’avantage de l’activation de l’exécution parallèle est plus coûteuse que l’accélération obtenue. Par conséquent, PLINQ ne pas parallélise automatiquement chaque requête. Il examine d’abord la forme de la requête et les différents opérateurs qui le composent. En fonction de cette analyse, PLINQ en mode d’exécution par défaut peut décider à exécuter tout ou partie de la requête de manière séquentielle. Toutefois, dans certains cas vous pouvez en savoir plus sur votre requête que PLINQ n’est pas en mesure de déterminer à partir de son analyse. Par exemple, vous savez qu’un délégué est très coûteux, et que la requête bénéficiera assurément de la parallélisation. Dans ce cas, vous pouvez utiliser la <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> (méthode) et spécifiez la <xref:System.Linq.ParallelExecutionMode.ForceParallelism> valeur pour indiquer à PLINQ de toujours exécuter la requête en parallèle.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Coupez et collez ce code dans le [données PLINQ, exemple](../../../docs/standard/parallel-programming/plinq-data-sample.md) et appelez la méthode à partir de `Main`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
