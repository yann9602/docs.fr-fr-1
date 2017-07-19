---
title: "How to: Control Ordering in a PLINQ Query | Microsoft Docs"
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
  - "PLINQ queries, how to control ordering"
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Control Ordering in a PLINQ Query
Ces exemples indiquent comment contrôler le classement dans une requête PLINQ à l'aide de la méthode d'extension <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
> [!WARNING]
>  Ces instances sont principalement destinées à montrer l'utilisation et peuvent ou non s'exécuter plus rapidement que les requêtes LINQ to Objects séquentielles équivalentes.  
  
## Exemple  
 L'exemple suivant conserve le classement de la séquence source.  Le classement est parfois nécessaire ; certains opérateurs de requête, par exemple, nécessitent qu'une séquence source classée produise des résultats corrects.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## Exemple  
 L'exemple suivant montre certains opérateurs de requête dont la séquence source est probablement supposée être classée.  Ces opérateurs fonctionneront avec des séquences non classées, mais peuvent alors produire des résultats inattendus.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Pour exécuter cette méthode, collez\-la dans la classe PLINQDataSample du projet [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) et appuyez sur F5.  
  
## Exemple  
 L'exemple suivant indique comment conserver le classement pour la première partie d'une requête, puis supprimer le classement pour augmenter la performance d'une clause join et réappliquer le classement à la séquence de résultat final.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Pour exécuter cette méthode, collez\-la dans la classe PLINQDataSample du projet [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) et appuyez sur F5.  
  
## Voir aussi  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)