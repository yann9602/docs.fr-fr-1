---
title: "How to: Enable Thread-Tracking Mode in SpinLock | Microsoft Docs"
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
  - "SpinLock, how to enable thread-tracking"
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Enable Thread-Tracking Mode in SpinLock
<xref:System.Threading.SpinLock?displayProperty=fullName> est un verrou d'exclusion mutuelle de bas niveau que vous pouvez utiliser pour les scénarios disposant de durées d'attente très courtes.  <xref:System.Threading.SpinLock> n'est pas ré\-entrant.  Une fois qu'un thread est entré dans le verrou, il doit le quitter correctement avant de pouvoir à nouveau entrer.  En général, toute tentative de ré\-entrer dans le verrou provoquerait un interblocage, et les interblocages peuvent être très difficiles à déboguer.  Pour faciliter le développement, <xref:System.Threading.SpinLock?displayProperty=fullName> prend en charge un mode de suivi de thread qui lève une exception lorsqu'un thread essaie de ré\-entrer dans un verrou qu'il contient déjà.  Cela vous permet de retrouver plus facilement le moment où le verrou n'a pas été quitté correctement.  Vous pouvez activer le mode de suivi de thread à l'aide du constructeur <xref:System.Threading.SpinLock> qui utilise un paramètre d'entrée booléen et en passant l'argument `true`.  Une fois que vous avez terminé les phases de développement et de test, désactivez le mode de suivi de thread pour de meilleures performances.  
  
## Exemple  
 Voici un exemple de mode de suivi de thread.  Les lignes qui permettent de quitter correctement le verrou sont commentées pour simuler une erreur de codage provoquant l'un des résultats suivants :  
  
-   Une exception est levée si le <xref:System.Threading.SpinLock> a été créé à l'aide de l'argument `true` \(`True` en Visual Basic\).  
  
-   Interblocage si le <xref:System.Threading.SpinLock> a été créé à l'aide de l'argument `false` \(`False` en Visual Basic\).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## Voir aussi  
 [SpinLock](../../../docs/standard/threading/spinlock.md)