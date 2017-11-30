---
title: "Comment : contrôler l'ordre dans une requête PLINQ"
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
helpviewer_keywords: PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9e29aa825a68154e32a34a23ca170258092b88a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Comment : contrôler l'ordre dans une requête PLINQ
Ces exemples montrent comment contrôler le classement dans une requête PLINQ à l’aide de la <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> méthode d’extension.  
  
> [!WARNING]
>  Ces exemples sont principalement destinés à illustrer l’utilisation et peuvent ou peut ne pas fonctionner plus rapidement que la LINQ séquentiel équivalentes aux requêtes d’objets.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant conserve l’ordre de la séquence source. Cela est parfois nécessaire ; par exemple, certains opérateurs de requête nécessitent une séquence ordonnée source pour produire des résultats corrects.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre certains opérateurs dont la séquence source est probablement prévue pour être classés de requête. Ces opérateurs fonctionneront sur les séquences non triées, mais ils peuvent produire des résultats inattendus.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Pour exécuter cette méthode, collez-la dans la classe PLINQDataSample du [données PLINQ, exemple](../../../docs/standard/parallel-programming/plinq-data-sample.md) de projet et appuyez sur F5.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment conserver le classement pour la première partie d’une requête, puis supprimer le classement à augmenter les performances d’une clause join et réappliquez le classement à la séquence de résultat final.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Pour exécuter cette méthode, collez-la dans la classe PLINQDataSample du [données PLINQ, exemple](../../../docs/standard/parallel-programming/plinq-data-sample.md) de projet et appuyez sur F5.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.ParallelEnumerable>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
