---
title: "How to: Listen for Cancellation Requests by Polling | Microsoft Docs"
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
  - "cancellation, how to poll for requests"
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# How to: Listen for Cancellation Requests by Polling
L'exemple suivant illustre une méthode permettant au code utilisateur d'interroger à intervalles réguliers un jeton d'annulation pour voir si l'annulation a été demandée par le thread appelant.  Cet exemple utilise le type <xref:System.Threading.Tasks.Task?displayProperty=fullName>, mais le même modèle s'applique aux opérations asynchrones créées directement par le type <xref:System.Threading.ThreadPool?displayProperty=fullName> ou le type <xref:System.Threading.Thread?displayProperty=fullName>.  
  
## Exemple  
 L'interrogation requiert un certain genre de boucle ou de code récursif qui peut lire régulièrement la valeur de la propriété booléenne <xref:System.Threading.CancellationToken.IsCancellationRequested%2A>.  Si vous utilisez le type <xref:System.Threading.Tasks.Task?displayProperty=fullName> et que vous attendez que la tâche se termine sur le thread appelant, vous pouvez utiliser la méthode <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> pour vérifier la propriété et lever l'exception.  En utilisant cette méthode, vous garantissez que l'exception correcte est levée en réponse à une demande.  Si vous utilisez un <xref:System.Threading.Tasks.Task>, l'appel à cette méthode est préférable à la levée manuelle d'un <xref:System.OperationCanceledException>.  Si vous n'avez pas à lever l'exception, vous pouvez simplement vérifier la propriété et le retour de la méthode si la propriété a la valeur `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 L'appel à <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> est extrêmement rapide et ne présente pas de charges mémoire significatives dans les boucles.  
  
 Si vous appelez <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, vous devez simplement vérifier explicitement la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> si vous avez un autre travail à faire en réponse à l'annulation, en plus de lever l'exception.  Dans cet exemple, vous pouvez voir que le code accède en fait deux fois à la propriété : une fois dans l'accès explicite et une nouvelle fois dans la méthode <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>.  Toutefois, comme l'opération de lecture de la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> implique une seule instruction de lecture volatile par accès, le double accès n'est pas significatif du point de vue des performances.  Il est toutefois préférable d'appeler la méthode plutôt que de lever manuellement <xref:System.OperationCanceledException>.  
  
## Voir aussi  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)