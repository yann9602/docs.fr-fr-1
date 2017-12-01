---
title: "Comment : écouter les demandes d'annulation par l'interrogation"
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
helpviewer_keywords: cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f0e05e3f66d591a28d7e84d358934959764dab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Comment : écouter les demandes d'annulation par l'interrogation
L’exemple suivant montre une façon de code utilisateur d’interroger un jeton d’annulation à intervalles réguliers pour voir si l’annulation a été demandée à partir du thread appelant. Cet exemple utilise le <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, mais le même modèle s’applique aux opérations asynchrones créées directement par le <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type ou le <xref:System.Threading.Thread?displayProperty=nameWithType> type.  
  
## <a name="example"></a>Exemple  
 L’interrogation requiert un certain genre de boucle ou code récursif qui peut lire régulièrement la valeur de la valeur booléenne <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriété. Si vous utilisez la <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> et vous sont en attente pour la tâche se termine sur le thread appelant, vous pouvez utiliser la <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> méthode pour vérifier la propriété et lever l’exception. À l’aide de cette méthode, vous assurez que l’exception correcte est levée en réponse à une demande. Si vous utilisez un <xref:System.Threading.Tasks.Task>, puis l’appel de cette méthode est préférable à la levée manuellement un <xref:System.OperationCanceledException>. Si vous n’êtes pas obligé de lever l’exception, vous pouvez simplement vérifier la propriété et le retour de la méthode si la propriété est `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Appel de <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> est extrêmement rapide et ne présente pas de surcharge importante dans les boucles.  
  
 Si vous appelez <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, vous avez uniquement à vérifier explicitement les <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriété si vous avez un autre travail à faire en réponse à l’annulation, en plus de lever l’exception. Dans cet exemple, vous pouvez voir que le code accède en fait deux fois à la propriété : une fois dans l’accès explicite et à nouveau dans le <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> (méthode). Mais étant donné que l’opération de lecture la <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriété implique une seule instruction par accès de lecture volatile, le double accès n’est pas significatif du point de vue des performances. Il est toujours préférable d’appeler la méthode plutôt que de lever manuellement le <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Voir aussi  
 [Annulation dans les threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md)
