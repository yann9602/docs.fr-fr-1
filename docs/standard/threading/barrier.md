---
title: "Barrier (.NET Framework) | Microsoft Docs"
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
  - "synchronization primitives, Barrier"
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Barrier (.NET Framework)
Un *cloisonnement* est une primitive de synchronisation définie par l'utilisateur qui permet à plusieurs threads \(appelés *participants*\) de travailler simultanément sur un algorithme en plusieurs phases.  Chaque participant s'exécute jusqu'à ce qu'il atteigne le point de cloisonnement dans le code.  Le cloisonnement représente la fin d'une phase de travail.  Quand un participant atteint le cloisonnement, il se bloque jusqu'à ce que tous les participants aient atteint le même cloisonnement.  Une fois que tous les participants ont atteint le cloisonnement, vous pouvez éventuellement appeler une action post\-phase.  Cette action post\-phase peut être utilisée pour effectuer des actions avec un thread unique alors que tous les autres threads sont encore bloqués.  Une fois l'action exécutée, tous les participants sont débloqués.  
  
 L'extrait de code suivant montre un modèle de cloisonnement de base.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Pour obtenir un exemple complet, voir [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## Ajout et suppression des participants  
 Quand vous créez un <xref:System.Threading.Barrier>, spécifiez le nombre de participants.  Vous pouvez également ajouter ou supprimer des participants dynamiquement à tout moment.  Par exemple, si un participant résout sa part du problème, vous pouvez stocker le résultat, arrêter l'exécution sur ce thread et appeler <xref:System.Threading.Barrier.RemoveParticipant%2A> pour décrémenter le nombre de participants du cloisonnement.  Quand vous ajoutez un participant en appelant <xref:System.Threading.Barrier.AddParticipant%2A>, la valeur de retour spécifie le numéro de la phase actuelle, ce qui peut être utile pour initialiser le travail du nouveau participant.  
  
## Cloisonnements cassés  
 Des blocages peuvent se produire si un participant ne parvient pas à atteindre le cloisonnement.  Pour éviter ces blocages, utilisez les surcharges de la méthode <xref:System.Threading.Barrier.SignalAndWait%2A> pour spécifier un délai d'attente et un jeton d'annulation.  Ces surcharges retournent une valeur booléenne que chaque participant peut vérifier avant de passer à la phase suivante.  
  
## Exceptions post\-phase  
 Si le délégué post\-phase lève une exception, il est encapsulé dans un objet <xref:System.Threading.BarrierPostPhaseException> qui est ensuite propagé à tous les participants.  
  
## Cloisonnement et ContinueWhenAll  
 Les cloisonnements sont particulièrement utiles quand les threads exécutent plusieurs phases dans des boucles.  Si votre code requiert uniquement une ou deux phases de travail, songez à utiliser des objets <xref:System.Threading.Tasks.Task?displayProperty=fullName> avec n'importe quel type de jointure implicite, notamment :  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 Pour plus d'informations, voir [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## Voir aussi  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)