---
title: "How to: Specify Merge Options in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, how to use merge options"
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Specify Merge Options in PLINQ
Cet exemple indique comment spécifier les options de fusion qui s'appliqueront à tous les opérateurs suivants dans une requête PLINQ.  Vous n'avez pas à définir les options de fusion explicitement, mais cela peut améliorer les performances.  Pour plus d'informations sur les options de fusion, consultez [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
>  Cet exemple est destiné à montrer l'utilisation et peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.  Pour plus d'informations sur l'accélération, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## Exemple  
 L'exemple suivant montre le comportement des options de fusion dans un scénario de base avec une source non classée et une fonction coûteuse à chaque élément.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 Dans les cas où l'option <xref:System.Linq.ParallelMergeOptions> entraîne une latence indésirable avant que le premier élément ne soit transmis, essayez l'option <xref:System.Linq.ParallelMergeOptions> pour transmettre les éléments de résultat plus rapidement et plus facilement.  
  
## Voir aussi  
 <xref:System.Linq.ParallelMergeOptions>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)