---
title: "Pausing and Resuming Threads | Microsoft Docs"
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
  - "resuming threads"
  - "threading [.NET Framework], pausing"
  - "pausing threads"
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Pausing and Resuming Threads
Les méthodes les plus courantes permettant de synchroniser les activités de threads consistent à bloquer et à diffuser des threads, ou à verrouiller des objets ou des régions du code.  Pour plus d'informations sur ces mécanismes de verrouillage et de blocage, voir [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Vous pouvez également avoir des threads en veille.  Quand des threads sont bloqués ou en veille, vous pouvez utiliser une <xref:System.Threading.ThreadInterruptedException> pour les débloquer ou les réveiller.  
  
## La méthode Thread.Sleep  
 L'appel de la méthode <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> entraîne le blocage immédiat du thread actuel pendant le nombre de millisecondes que dure le passage à <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>, cédant ainsi le reste de sa tranche temporelle à un autre thread.  Un thread ne peut pas appeler <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> sur un autre thread.  
  
 L'appel de <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> avec <xref:System.Threading.Timeout.Infinite?displayProperty=fullName> entraîne la mise en veille du thread jusqu'à ce qu'il soit interrompu par un autre thread qui appelle <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName>, ou jusqu'à ce qu'il soit terminé par <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>.  
  
## Interruption de threads  
 Vous pouvez interrompre un thread en attente en appelant <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> sur le thread bloqué pour lever une <xref:System.Threading.ThreadInterruptedException>, ce qui retirera le thread de l'appel bloquant.  Le thread doit intercepter la <xref:System.Threading.ThreadInterruptedException> et faire tout le nécessaire pour continuer à fonctionner.  Si le thread ignore l'exception, le runtime intercepte l'exception et arrête le thread.  
  
> [!NOTE]
>  Si le thread cible n'est pas bloqué quand <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> est appelé, le thread ne sera pas interrompu avant d'être bloqué.  Si le thread n'est jamais bloqué, il peut se terminer sans jamais être interrompu.  
  
 En cas d'attente managée, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> et <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> réveillent le thread immédiatement.  En cas d'attente non managée \(par exemple, dans le cas d'un appel de code non managé à la fonction Win32 `WaitForSingleObject`\), ni <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> ni <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> ne pourront prendre le contrôle du thread tant qu'il ne sera pas retourné dans du code managé ou tant qu'il n'effectuera pas d'appel depuis du code managé.  Dans du code managé, le comportement est le suivant :  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> réveille un thread en attente et provoque la levée d'une <xref:System.Threading.ThreadInterruptedException> dans le thread de destination.  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> est semblable à <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName>, à la différence près qu'il entraîne la levée d'une <xref:System.Threading.ThreadAbortException> sur le thread.  Pour plus d'informations, voir [Destruction de threads](../../../docs/standard/threading/destroying-threads.md).  
  
## Interruption et reprise \(obsolète\)  
 La classe <xref:System.Threading.Thread> comprend deux méthodes, <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> et <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName>, pour l'interruption et la reprise d'un thread.  Toutefois, l'utilisation de ces méthodes n'est pas recommandée.  
  
> [!IMPORTANT]
>  Dans .NET Framework version 2.0 et ultérieures, les méthodes <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> et <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> sont obsolètes et seront supprimées dans une prochaine version.  
>   
>  Les méthodes <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> et <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> ne sont généralement pas utiles pour les applications et ne doivent pas être confondues avec les mécanismes de synchronisation.  Étant donné que <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> et <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> ne reposent pas sur la coopération du thread contrôlé, ils sont très intrusifs et peuvent générer de graves problèmes d'application comme des interblocages \(par exemple, si vous interrompez un thread qui détient une ressource dont un autre thread a besoin\).  
  
 Certaines applications ont besoin de contrôler la priorité des threads pour optimiser les performances.  Pour ce faire, vous devez utiliser la propriété <xref:System.Threading.Thread.Priority%2A?displayProperty=fullName> plutôt que <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadInterruptedException>   
 <xref:System.Threading.ThreadAbortException>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)   
 [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)