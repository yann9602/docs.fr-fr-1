---
title: "How to: Use SpinLock for Low-Level Synchronization | Microsoft Docs"
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
  - "SpinLock, how to use"
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Use SpinLock for Low-Level Synchronization
L'exemple suivant montre comment utiliser un <xref:System.Threading.SpinLock>.  
  
## Exemple  
 Dans cet exemple, la section critique exécute une quantité minimale de travail, ce qui en fait un bon candidat pour un <xref:System.Threading.SpinLock>.  La légère augmentation de la quantité de travail améliore les performances du <xref:System.Threading.SpinLock>, comparé à un verrou standard.  Toutefois, au\-delà d'un certain point, un verrouillage tournant devient plus coûteux qu'un verrou standard.  Vous pouvez utiliser la nouvelle fonctionnalité de profilage d'accès concurrentiel pour savoir quel type de verrou fournit les meilleures performances pour votre programme.  Pour plus d'informations, consultez [Visualiseur concurrence](../Topic/Concurrency%20Visualizer.md).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> peut être utile lorsqu'un verrou placé sur une ressource partagée ne doit pas être maintenu très longtemps.  Dans ce cas, sur les ordinateurs multicœurs, il peut être efficace pour le thread bloqué de tourner pendant quelques cycles jusqu'à ce que le verrou soit libéré.  En tournant, le thread ne se bloque pas, ce qui est un processus gourmand en ressources processeur.  <xref:System.Threading.SpinLock> cessera de tourner sous certaines conditions pour empêcher la privation des processeurs logiques ou l'inversion de priorité sur les systèmes équipés de la technologie Hyper\-Threading.  
  
 Cet exemple utilise la classe <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>, qui requiert la synchronisation utilisateur pour l'accès multithread.  Dans les applications qui ciblent .NET Framework 4, une autre option consiste à utiliser le <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>, qui ne requiert aucun verrouillage utilisateur.  
  
 Notez l'utilisation de `false` \(`False` en Visual Basic\) dans l'appel à <xref:System.Threading.SpinLock.Exit%2A>.  Cela fournit de meilleures performances.  Spécifiez `true` \(`True`\) sur les architectures IA64 pour utiliser la barrière mémoire, qui vide les mémoires tampons d'écriture pour vérifier que les autres threads peuvent désormais quitter le verrou.  
  
## Voir aussi  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)