---
title: "Thread.Suspend, Garbage Collection, and Safe Points | Microsoft Docs"
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
  - "suspending threads"
  - "safe points"
  - "threading [.NET Framework], suspending"
  - "threading [.NET Framework], garbage collection"
  - "garbage collection, threads"
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Thread.Suspend, Garbage Collection, and Safe Points
Lorsque vous appelez <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> sur un thread, le système remarque la demande d'interruption de thread et permet au thread de s'exécuter jusqu'à ce qu'il atteigne un point sans risque avant d'interrompre le thread.  Un point sans risque pour un thread correspond à un point dans son exécution où il est possible d'effectuer un garbage collection.  
  
 Une fois qu'un point sans risque a été atteint, le runtime garantit que le thread suspendu ne fera pas plus de progrès dans le code managé.  Un thread qui s'exécute en dehors du code managé est toujours sans risque pour un garbage collection, et son exécution se poursuit jusqu'à ce qu'il tente de reprendre l'exécution du code managé.  
  
> [!NOTE]
>  Afin d'effectuer un garbage collection, le runtime doit suspendre tous les threads \- sauf le thread qui effectue la collection.  Chaque thread doit être acheminé vers un point sans risque avant d'être suspendu.  
  
## Voir aussi  
 <xref:System.Threading.Thread>   
 <xref:System.GC>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Gestion automatique de la mémoire](../../../docs/standard/automatic-memory-management.md)