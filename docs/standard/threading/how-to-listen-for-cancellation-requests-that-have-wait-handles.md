---
title: "How to: Listen for Cancellation Requests That Have Wait Handles | Microsoft Docs"
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
  - "cancellation, waiting with wait handles"
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Listen for Cancellation Requests That Have Wait Handles
Si une méthode est bloquée pendant qu'elle attend qu'un événement soit signalé, elle ne peut pas vérifier la valeur du jeton d'annulation et répondre en temps voulu.  Le premier exemple montre comment résoudre ce problème lorsque vous travaillez avec des événements tels que <xref:System.Threading.ManualResetEvent?displayProperty=fullName> qui ne prennent pas en charge l'infrastructure d'annulation unifiée en mode natif.  Le deuxième exemple présente une approche plus simplifiée qui utilise <xref:System.Threading.ManualResetEventSlim?displayProperty=fullName>, lequel prend en charge l'annulation unifiée.  
  
> [!NOTE]
>  Lorsque l'option "Uniquement mon code" est activée, Visual Studio s'arrête dans certains cas sur la ligne qui lève l'exception et affiche un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est bénigne.  Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions illustré dans les exemples ci\-dessous.  Pour empêcher Visual Studio de s'arrêter sur la première erreur, il vous suffit de désactiver la case à cocher "Uniquement mon code" sous **Outils, Options, Débogage, Général**.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Threading.ManualResetEvent> pour montrer comment débloquer des handles d'attente qui ne prennent pas en charge l'annulation unifiée.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Threading.ManualResetEventSlim> pour montrer comment débloquer des primitives de coordination qui prennent en charge l'annulation unifiée.  Les techniques décrites peuvent également être utilisées avec autres primitives de coordination simplifiées, telles que <xref:System.Threading.Semaphore>`Slim` et <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## Voir aussi  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)