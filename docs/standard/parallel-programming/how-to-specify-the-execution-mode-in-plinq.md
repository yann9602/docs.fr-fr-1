---
title: "How to: Specify the Execution Mode in PLINQ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PLINQ queries, how to use execution mode"
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Specify the Execution Mode in PLINQ
Cet exemple indique comment forcer PLINQ à ignorer sa méthode heuristique par défaut et paralléliser une requête indépendamment de sa forme.  
  
> [!WARNING]
>  Cet exemple est destiné à montrer l'utilisation et peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.  Pour plus d'informations sur l'accélération, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## Exemple  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ est conçu pour exploiter des possibilités de parallélisation  Toutefois, l'exécution parallèle ne convient pas à toutes les requêtes.  Par exemple, lorsqu'une requête contient un délégué mono\-utilisateur qui exécute très peu de travail, une exécution séquentielle est en général plus rapide.  La raison en est la surcharge impliquée par l'activation de l'exécution parallèle, qui se révèle plus coûteuse que l'accélération obtenue.  Par conséquent, PLINQ ne parallélise pas automatiquement toutes les requêtes.  Il examine d'abord la forme de la requête et les différents opérateurs dont elle composée.  Sur la base de cette analyse, PLINQ, en mode d'exécution par défaut, peut décider d'exécuter certaines ou toutes les requêtes séquentiellement.  Toutefois, dans certains cas, vous pouvez en savoir plus sur votre requête que PLINQ n'est en mesure de déterminer d'après son analyse.  Par exemple, vous pouvez savoir qu'un délégué est très coûteux et que la requête bénéficiera assurément de la parallélisation.  Dans les tels cas, vous pouvez utiliser la méthode <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> et spécifier la valeur <xref:System.Linq.ParallelExecutionMode> pour indiquer à PLINQ de toujours exécuter la requête comme une requête parallèle.  
  
## Compilation du code  
 Copiez et collez ce code dans l'exemple de données PLINQ \([PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md)\) et appelez la méthode depuis `Main`.  
  
## Voir aussi  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)