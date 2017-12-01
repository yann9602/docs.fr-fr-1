---
title: "Comment : écouter plusieurs demandes d'annulation"
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
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36cf338a15ad3f7d234f902c50a2dbb1b2e95847
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Comment : écouter plusieurs demandes d'annulation
Cet exemple montre comment écouter simultanément deux jetons d’annulation afin que vous pouvez annuler une opération si des jetons le demande.  
  
> [!NOTE]
>  Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s’arrêter sur la première erreur, il suffit de désactiver la case à cocher « Uniquement mon Code » sous **outils, Options, débogage, général**.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> méthode est utilisée pour joindre deux jetons dans un jeton. Ainsi, le jeton à passer aux méthodes qui prennent l’annulation qu’un seul jeton en tant qu’argument. L’exemple illustre un scénario courant dans lequel une méthode doit observer à la fois un jeton passé depuis en dehors de la classe et un jeton généré à l’intérieur de la classe.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Lorsque le jeton lié lève un <xref:System.OperationCanceledException>, le jeton qui est passé à l’exception est le jeton lié, et non un des jetons prédécesseurs. Pour déterminer quel jeton a été annulé, vérifiez l’état des jetons prédécesseurs directement.  
  
 Dans cet exemple, <xref:System.AggregateException> ne doit jamais être levée, mais il est intercepté ici car dans les scénarios réels toutes les autres exceptions excepté <xref:System.OperationCanceledException> qui sont levées à partir du délégué de tâche sont encapsulés dans un <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Voir aussi  
 [Annulation dans les threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md)
