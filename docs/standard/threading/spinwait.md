---
title: "SpinWait | Microsoft Docs"
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
  - "synchronization primitives, SpinWait"
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# SpinWait
<xref:System.Threading.SpinWait?displayProperty=fullName> est un type de synchronisation léger que vous pouvez utiliser dans des scénarios de bas niveau pour éviter les changements de contexte et les transitions de noyau complexes requis pour les événements de noyau.  Sur les ordinateurs multicœurs, lorsqu'une ressource ne doit pas être conservée pendant longtemps, il peut être plus efficace pour un thread en attente de tourner en mode utilisateur pendant quelques douzaines ou centaines de cycles, puis de réessayer d'acquérir la ressource.  Si la ressource est disponible après rotation, vous avez économisé plusieurs milliers de cycles.  Si la ressource n'est toujours pas disponible, vous n'avez utilisé que quelques cycles et pouvez encore entrer une attente basée sur le noyau.  Cette combinaison rotation, puis attente est parfois appelée *opération d'attente à deux phases*.  
  
 <xref:System.Threading.SpinWait> est conçu pour être utilisé avec les types .NET Framework qui incluent dans un wrapper des événements de noyau tels que <xref:System.Threading.ManualResetEvent>.  <xref:System.Threading.SpinWait> peut également être utilisé par lui\-même pour des fonctionnalités de rotation de base dans un seul programme.  
  
 <xref:System.Threading.SpinWait> est plus qu'une simple boucle vide.  Il est implémenté avec soin pour fournir un comportement de rotation correct pour les cas généraux et initialise lui\-même des changements de contexte s'il tourne assez longtemps \(environ la durée requise pour une transition de noyau\).  Par exemple, sur les ordinateurs à cœur unique, <xref:System.Threading.SpinWait> génère immédiatement la tranche horaire du thread car la rotation bloque la progression sur tous les threads.  <xref:System.Threading.SpinWait> génère même sur les ordinateurs multicœurs pour empêcher le thread en attente de bloquer des threads de priorité plus élevée ou le garbage collector.  Par conséquent, si vous utilisez un <xref:System.Threading.SpinWait> dans une opération d'attente à deux phases, nous vous recommandons d'appeler l'attente de noyau avant que le <xref:System.Threading.SpinWait> lui\-même n'initialise un changement de contexte.  <xref:System.Threading.SpinWait> fournit la propriété <xref:System.Threading.SpinWait.NextSpinWillYield%2A>, que vous pouvez vérifier avant chaque appel à <xref:System.Threading.SpinWait.SpinOnce%2A>.  Lorsque la propriété retourne la valeur `true`, initialisez votre propre opération d'attente.  Pour obtenir un exemple, consultez [How to: Use SpinWait to Implement a Two\-Phase Wait Operation](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Si vous n'exécutez pas d'opération d'attente à deux phases mais que vous tournez simplement en attendant qu'une condition soit remplie, vous pouvez permettre à <xref:System.Threading.SpinWait> d'effectuer ses changements de contexte afin d'être un bon citoyen de l'environnement de système d'exploitation Windows.  L'exemple de base suivant montre un <xref:System.Threading.SpinWait> dans une pile sans verrou.  Si vous avez besoin d'une pile thread\-safe haute performance, envisagez d'utiliser <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## Voir aussi  
 <xref:System.Threading.Thread.SpinWait%2A>   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)