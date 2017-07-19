---
title: "How to: Combine Parallel and Sequential LINQ Queries | Microsoft Docs"
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
  - "parallel queries, combine parallel and sequential"
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Combine Parallel and Sequential LINQ Queries
Cet exemple indique comment utiliser la méthode <xref:System.Linq.ParallelEnumerable.AsSequential%2A> pour indiquer à PLINQ de traiter séquentiellement tous les opérateurs suivants dans la requête.  Bien que le traitement séquentiel soit généralement plus lent que le traitement parallèle, il est quelquefois nécessaire pour produire des résultats corrects.  
  
> [!WARNING]
>  Cet exemple est destiné à montrer l'utilisation et peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.  Pour plus d'informations sur l'accélération, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## Exemple  
 L'exemple suivant affiche un scénario dans lequel <xref:System.Linq.ParallelEnumerable.AsSequential%2A> est obligatoire, pour conserver le classement établi dans une clause précédente de la requête.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## Compilation du code  
 Pour compiler et exécuter ce code, collez\-le dans le projet [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md), ajoutez une ligne pour appeler la méthode à partir de `Main`, puis appuyez sur F5.  
  
## Voir aussi  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)