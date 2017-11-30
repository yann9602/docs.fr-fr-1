---
title: "Comment : spécifier des options de fusion en PLINQ"
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
helpviewer_keywords: PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec601e8bbefd31650fb91c438b032942cfc93101
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Comment : spécifier des options de fusion en PLINQ
Cet exemple montre comment spécifier les options de fusion qui seront appliquent à tous les opérateurs suivants dans une requête PLINQ. Il est inutile de définir explicitement les options de fusion, mais cela peut améliorer les performances. Pour plus d’informations sur les options de fusion, consultez [les Options de fusion en PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
>  Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre le comportement des options de fusion dans un scénario de base qui a une source non ordonnée et s’applique une fonction coûteuse à chaque élément.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 Dans le cas où la <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option entraîne une latence indésirable avant le premier élément est transmis, essayez du <xref:System.Linq.ParallelMergeOptions.NotBuffered> option pour générer des éléments de résultat plus rapidement et plus facilement.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.ParallelMergeOptions>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
