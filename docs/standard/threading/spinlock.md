---
title: "SpinLock | Microsoft Docs"
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
  - "synchronization primitives, SpinLock"
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# SpinLock
La structure <xref:System.Threading.SpinLock> est une primitive de synchronisation de bas niveau et à exclusion mutuelle qui tourne en attendant d'acquérir un verrou.  Sur les ordinateurs à plusieurs cœurs, lorsque les temps d'attente sont supposés être courts et que le conflit est minime, <xref:System.Threading.SpinLock> peut être plus performant que d'autres genres de verrous.  Toutefois, nous vous recommandons d'utiliser <xref:System.Threading.SpinLock> uniquement lorsque vous déterminez par profilage que les méthodes <xref:System.Threading.Monitor?displayProperty=fullName> ou <xref:System.Threading.Interlocked> ralentissent considérablement les performances de votre programme.  
  
 <xref:System.Threading.SpinLock> peut rapporter la tranche horaire du thread même s'il n'a pas encore acquis le verrou.  Il effectue cette opération pour éviter toute inversion de priorité de thread et permettre au garbage collector de poursuivre la progression.  Lorsque vous utilisez un <xref:System.Threading.SpinLock>, vérifiez qu'aucun thread ne peut détenir le verrou au\-delà d'un intervalle de temps très bref et qu'aucun thread ne peut se bloquer pendant qu'il détient le verrou.  
  
 Étant donné que le verrouillage spinlock est un type valeur, vous devez le passer explicitement par référence si vous prévoyez que les deux copies fassent référence au même verrou.  
  
 Pour plus d'informations sur l'utilisation de ce type, consultez <xref:System.Threading.SpinLock?displayProperty=fullName>.  Pour obtenir un exemple, consultez [How to: Use SpinLock for Low\-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock> prend en charge un mode de *suivi* de *threads* que vous pouvez utiliser pendant la phase de développement pour suivre le thread qui détient le verrou à un moment particulier.  Le mode de suivi de threads est très utile pour le débogage, mais nous vous recommandons de le désactiver dans la version Release de votre programme étant donné qu'il peut entraîner un ralentissement des performances.  Pour plus d'informations, consultez [How to: Enable Thread\-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## Voir aussi  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)