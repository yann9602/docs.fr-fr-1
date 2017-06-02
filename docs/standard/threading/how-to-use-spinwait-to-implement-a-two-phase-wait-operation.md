---
title: "How to: Use SpinWait to Implement a Two-Phase Wait Operation | Microsoft Docs"
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
  - "SpinWait, how to synchronize two-phase wait"
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Use SpinWait to Implement a Two-Phase Wait Operation
L'exemple suivant montre comment utiliser un objet <xref:System.Threading.SpinWait?displayProperty=fullName> pour implémenter une opération d'attente à deux phases.  Au cours de la première phase, l'objet de synchronisation, un `Latch`, tourne pendant quelques cycles pendant qu'il vérifie si le verrou est devenu disponible.  Au cours de la deuxième phase, si le verrou devient disponible, la méthode `Wait` est retournée sans utiliser le <xref:System.Threading.ManualResetEvent?displayProperty=fullName> pour exécuter son attente ; sinon, `Wait` exécute l'attente.  
  
## Exemple  
 Cet exemple montre une implémentation de base d'une primitive de synchronisation de verrou interne.  Vous pouvez utiliser cette structure de données lorsque les temps d'attente sont supposés être très courts.  Cet exemple est fourni à des fins de démonstration uniquement.  Si vous avez besoin de fonctionnalités de type de verrou dans votre programme, envisagez d'utiliser <xref:System.Threading.ManualResetEventSlim?displayProperty=fullName>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Le verrou utilise l'objet <xref:System.Threading.SpinWait> pour tourner sur place uniquement jusqu'à que l'appel suivant à `SpinOnce` entraîne le <xref:System.Threading.SpinWait> à générer la tranche horaire du thread.  À ce stade, le verrou provoque son propre changement de contexte en appelant <xref:System.Threading.WaitHandle.WaitOne%2A> sur le <xref:System.Threading.ManualResetEvent> et en passant le reste de la valeur du délai d'attente.  
  
 La sortie d'enregistrement indique à quelle fréquence le verrou interne était en mesure d'améliorer les performances en acquérant le verrou sans utiliser le <xref:System.Threading.ManualResetEvent>.  
  
## Voir aussi  
 [SpinWait](../../../docs/standard/threading/spinwait.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)