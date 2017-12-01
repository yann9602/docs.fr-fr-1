---
title: "Comment : écouter les demandes d'annulation avec des handles d'attente"
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
helpviewer_keywords: cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1eaa84d924fde63e94c36fab50a809c7c03f075
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Comment : écouter les demandes d'annulation avec des handles d'attente
Si une méthode est bloquée lorsqu’elle est en attente d’un événement soit signalé, il ne peut pas vérifier la valeur de jeton d’annulation et répondre en temps voulu. Le premier exemple montre comment résoudre ce problème lorsque vous travaillez avec des événements tels que <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> qui ne prennent pas en charge l’infrastructure d’annulation unifiée. Le deuxième exemple montre une approche plus simple qui utilise <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, qui prend en charge l’annulation unifiée.  
  
> [!NOTE]
>  Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s’arrêter sur la première erreur, il suffit de désactiver la case à cocher « Uniquement mon Code » sous **outils, Options, débogage, général**.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un <xref:System.Threading.ManualResetEvent> pour montrer comment débloquer des handles d’attente qui ne prennent pas en charge l’annulation unifiée.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un <xref:System.Threading.ManualResetEventSlim> pour montrer comment débloquer la coordination primitives qui prennent en charge l’annulation d’unifiée. La même approche peut être utilisée avec les autres primitives de coordination simplifiées, telles que <xref:System.Threading.Semaphore> `Slim` et <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Voir aussi  
 [Annulation dans les threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md)
