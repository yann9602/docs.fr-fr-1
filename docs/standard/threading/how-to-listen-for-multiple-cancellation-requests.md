---
title: "How to: Listen for Multiple Cancellation Requests | Microsoft Docs"
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
  - "cancellation tokens, joining"
  - "LinkedTokenSource, how to"
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Listen for Multiple Cancellation Requests
Cet exemple montre comment écouter simultanément deux jetons d'annulation afin de pouvoir annuler une opération si l'un des jetons le demande.  
  
> [!NOTE]
>  Lorsque l'option "Uniquement mon code" est activée, Visual Studio s'arrête dans certains cas sur la ligne qui lève l'exception et affiche un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est bénigne.  Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions illustré dans les exemples ci\-dessous.  Pour empêcher Visual Studio de s'arrêter sur la première erreur, il vous suffit de désactiver la case à cocher "Uniquement mon code" sous **Outils, Options, Débogage, Général**.  
  
## Exemple  
 Dans l'exemple suivant, la méthode <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> est utilisée pour joindre deux jetons dans un jeton.  Cela permet au jeton d'être passé à des méthodes qui prennent uniquement un jeton d'annulation comme argument.  L'exemple présente un scénario courant dans lequel une méthode doit observer à la fois un jeton passé depuis l'extérieur de la classe et un jeton généré à l'intérieur de la classe.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Lorsque le jeton lié lève un <xref:System.OperationCanceledException>, le jeton qui est passé à l'exception est le jeton lié, et non l'un des jetons prédécesseurs.  Pour déterminer quel jeton a été annulé, vérifiez directement l'état des jetons prédécesseurs.  
  
 Dans cet exemple, <xref:System.AggregateException> ne devrait jamais être levé, mais il est intercepté ici car dans les scénarios réels, toutes les autres exceptions excepté <xref:System.OperationCanceledException> qui sont levées à partir du délégué de tâche sont incluses dans un wrapper dans un <xref:System.OperationCanceledException>.  
  
## Voir aussi  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)