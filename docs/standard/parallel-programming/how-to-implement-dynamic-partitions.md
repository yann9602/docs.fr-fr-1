---
title: "How to: Implement Dynamic Partitions | Microsoft Docs"
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
  - "tasks, how to create a dynamic partitioner"
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# How to: Implement Dynamic Partitions
L'exemple suivant illustre comment implémenter un <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=fullName> personnalisé qui implémente le partitionnement dynamique et peut être utilisé à partir de certaines surcharges <xref:System.Threading.Tasks.Parallel.ForEach%2A> et à partir de PLINQ.  
  
## Exemple  
 Chaque fois qu'une partition appelle <xref:System.Collections.IEnumerator.MoveNext%2A> sur l'énumérateur, l'énumérateur fournit la partition avec un élément de liste.  Dans le cas de PLINQ et de <xref:System.Threading.Tasks.Parallel.ForEach%2A>, la partition est une instance <xref:System.Threading.Tasks.Task>.  Étant donné que les requêtes arrivent simultanément sur plusieurs threads, l'accès à l'index actuel est synchronisé.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 Il s'agit d'un exemple de partitionnement par segments, avec chaque segment qui se compose d'un élément.  En fournissant plus d'éléments à la fois, vous pourriez réduire le conflit sur le verrou et théoriquement atteindre des performances plus rapides.  Toutefois, à un certain moment, les plus grands segments peuvent nécessiter une logique d'équilibrage de charge supplémentaire pour maintenir tous les threads occupés jusqu'à ce que tout le travail soit fait.  
  
## Voir aussi  
 [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)   
 [How to: Implement a Partitioner for Static Partitioning](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)