---
title: "How to: Write a Custom PLINQ Aggregate Function | Microsoft Docs"
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
  - "PLINQ queries, how to create aggregate function"
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Write a Custom PLINQ Aggregate Function
Cet exemple indique comment utiliser la méthode <xref:System.Linq.ParallelEnumerable.Aggregate%2A> pour appliquer une fonction d'agrégation personnalisée à une séquence source.  
  
> [!WARNING]
>  Cet exemple est destiné à montrer l'utilisation et peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.  Pour plus d'informations sur l'accélération, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## Exemple  
 L'exemple suivant calcule l'écart type d'une séquence d'entiers.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 Cet exemple utilise une surcharge de l'opérateur de requête standard d'agrégation qui est unique à PLINQ.  Cette surcharge prend un <xref:System.Func%603?displayProperty=fullName> supplémentaire comme troisième paramètre d'entrée.  Ce délégué combine les résultats de tous les threads avant d'exécuter le dernier calcul sur les résultats groupés.  Dans cet exemple, nous ajoutons les sommes de tous les threads.  
  
 Notez que lorsqu'un corps d'expression lambda se compose d'une expression unique, la valeur de retour du délégué <xref:System.Func%602?displayProperty=fullName> est la valeur de l'expression.  
  
## Voir aussi  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)