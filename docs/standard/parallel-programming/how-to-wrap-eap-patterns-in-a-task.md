---
title: "How to: Wrap EAP Patterns in a Task | Microsoft Docs"
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
  - "tasks, how to wrap EAP patterns"
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Wrap EAP Patterns in a Task
L'exemple suivant illustre l'exposition d'une séquence aléatoire de modèle asynchrone basé sur les événements EAP \(Extensible Authentication Protocol\) hôtes comme tâche unique à l'aide d'une classe <xref:System.Threading.Tasks.TaskCompletionSource%601> Cet exemple indique également comment utiliser <xref:System.Threading.CancellationToken> pour appeler les méthodes d'annulation intégrées sur les objets <xref:System.Net.WebClient>.  
  
## Exemple  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## Voir aussi  
 [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)