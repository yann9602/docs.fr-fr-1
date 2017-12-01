---
title: "Comment : gérer des exceptions dans une requête PLINQ"
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
helpviewer_keywords: PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 209e0c1bf89f231d03647ae4351279bfdb172e68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Comment : gérer des exceptions dans une requête PLINQ
Le premier exemple dans cette rubrique montre comment gérer les <xref:System.AggregateException?displayProperty=nameWithType> qui peut être levée à partir d’une requête PLINQ lors de son exécution. Le deuxième exemple montre comment mettre les blocs try-catch dans des délégués, aussi proche que possible pour où l’exception est levée. De cette façon, vous pouvez les intercepter dès qu’ils se produisent et que vous souhaitez continuer l’exécution des requêtes. Lorsque les exceptions sont autorisées à se propager vers le thread lié, il est possible qu'une requête puisse continuer à traiter des éléments après que l'exception ait été levée.  
  
 Dans certains cas lorsque PLINQ revient à l’exécution séquentielle et qu’une exception se produit, l’exception peut être propagée directement et non encapsulée dans un <xref:System.AggregateException>. En outre, <xref:System.Threading.ThreadAbortException>s sont toujours propagées directement.  
  
> [!NOTE]
>  Lorsque « Uniquement mon Code » est activée, Visual Studio s’arrête sur la ligne qui lève l’exception et afficher un message d’erreur indiquant que « exception pas gérée par le code utilisateur. » Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s’arrêter sur la première erreur, il suffit de désactiver la case à cocher « Uniquement mon Code » sous **outils, Options, débogage, général**.  
>   
>  Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment mettre les blocs try-catch autour du code qui exécute la requête pour intercepter toute <xref:System.AggregateException?displayProperty=nameWithType>s qui sont levées.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 Dans cet exemple, la requête ne peut pas continuer une fois que l’exception est levée. Au moment où que votre code d’application intercepte l’exception, PLINQ a déjà arrêté la requête sur tous les threads.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment placer un bloc try-catch dans un délégué pour rendre possible intercepter une exception et continuer l’exécution des requêtes.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler et exécuter ces exemples, copiez-les dans l’exemple de données PLINQ et appelez la méthode à partir de Main.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Ne pas intercepter une exception, sauf si vous savez comment gérer pour ne pas endommager l’état de votre programme.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.ParallelEnumerable>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
