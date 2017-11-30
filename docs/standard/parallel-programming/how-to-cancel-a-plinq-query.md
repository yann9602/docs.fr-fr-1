---
title: "Comment : annuler une requête PLINQ"
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
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8031758462df45c030b8b75a3507f1bfb44bfd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-plinq-query"></a>Comment : annuler une requête PLINQ
Les exemples suivants montrent deux façons d’annuler une requête PLINQ. Le premier exemple montre comment annuler une requête qui se compose principalement de parcours de données. Le deuxième exemple montre comment annuler une requête qui contient une fonction de l’utilisateur qui sollicite.  
  
> [!NOTE]
>  Lorsque « Uniquement mon Code » est activée, Visual Studio s’arrête sur la ligne qui lève l’exception et afficher un message d’erreur indiquant que « exception pas gérée par le code utilisateur. » Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s’arrêter sur la première erreur, il suffit de désactiver la case à cocher « Uniquement mon Code » sous **outils, Options, débogage, général**.  
>   
>  Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 L’infrastructure PLINQ ne restaure pas un seul <xref:System.OperationCanceledException> dans un <xref:System.AggregateException?displayProperty=nameWithType>; le <xref:System.OperationCanceledException> doit être gérée dans un bloc catch séparé. Si un ou plusieurs délégués utilisateurs lèvent un OperationCanceledException (à l’aide d’un externe <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), mais aucune autre exception et que la requête a été défini en tant que `AsParallel().WithCancellation(externalCT)`, PLINQ émettra un seul <xref:System.OperationCanceledException> (externalCT) plutôt qu’une <xref:System.AggregateException?displayProperty=nameWithType>. Toutefois, si un délégué utilisateur lève un <xref:System.OperationCanceledException>et un autre délégué lève un autre type d’exception, puis les deux exceptions seront restaurées dans un <xref:System.AggregateException>.  
  
 Les instructions générales sur l’annulation sont la suivante :  
  
1.  Si vous exécutez une annulation de délégué utilisateur vous devez informer PLINQ externe <xref:System.Threading.CancellationToken> et lever une <xref:System.OperationCanceledException>(externalCT).  
  
2.  Si l’annulation se produit et aucuns autres exceptions ne sont levées, puis vous devez gérer un <xref:System.OperationCanceledException> plutôt que <xref:System.AggregateException>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment gérer l’annulation lorsque vous avez une fonction de ressources de calcul dans le code utilisateur.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Lorsque vous gérez l’annulation dans le code utilisateur, vous n’avez pas à utiliser <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> dans la définition de requête. Toutefois, nous vous recommandons de procéder ainsi car <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> n’a aucun effet sur les performances des requêtes et permet l’annulation d’être gérés par des opérateurs de requête et votre code utilisateur.  
  
 Afin de garantir la réactivité du système, nous vous recommandons de vérifier les annulations par milliseconde ; Toutefois, une période jusqu'à 10 millisecondes est considérée comme acceptable. Cette fréquence ne doit pas avoir un impact négatif sur les performances de votre code.  
  
 Lorsqu’un énumérateur est supprimé, par exemple lorsque le code quitte une boucle foreach (For Each en Visual Basic) qui itère au sein des résultats de requête, la requête est annulée, mais aucune exception n’est levée.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.ParallelEnumerable>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Annulation dans les threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md)
