---
title: "Canceling Threads Cooperatively | Microsoft Docs"
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
  - "threads, cancellation"
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Canceling Threads Cooperatively
Avant [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework n’offrait aucune fonction intégrée permettant d’annuler, de manière coopérative, un thread après son démarrage. Toutefois, dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez utiliser des jetons d’annulation pour annuler les threads, tout comme vous pouvez les utiliser pour annuler les objets <xref:System.Threading.Tasks.Task?displayProperty=fullName> ou les requêtes PLINQ. Bien que la classe <xref:System.Threading.Thread?displayProperty=fullName> n’offre pas de prise en charge intégrée pour les jetons d’annulation, vous pouvez transmettre un jeton à une procédure de thread à l’aide du constructeur <xref:System.Threading.Thread> qui prend un délégué <xref:System.Threading.ParameterizedThreadStart>. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## Voir aussi  
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)