---
title: "Scheduling Threads | Microsoft Docs"
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
  - "threading [.NET Framework], scheduling"
  - "scheduling threads"
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Scheduling Threads
Chaque thread possède une priorité de thread qui lui est assignée.  La priorité **ThreadPriority.Normal** est affectée initialement aux threads créés dans le Common Language Runtime.  Les threads créés à l'extérieur du runtime conservent la priorité qu'ils avaient avant d'entrer dans l'environnement managé.  Vous pouvez obtenir ou définir la priorité de n'importe quel thread à l'aide de la propriété **Thread.Priority**.  
  
 La planification de l'exécution des threads est fondée sur leur priorité.  Même si les threads sont exécutés au sein du runtime, le système d'exploitation assigne à tous les threads des tranches de temps processeur.  Les informations de l'algorithme de planification utilisées pour déterminer l'ordre d'exécution des threads dépendent du système d'exploitation.  Sous certains systèmes d'exploitation, le thread possédant la priorité la plus élevée \(parmi les threads qui peuvent s'exécuter\) est toujours planifié pour s'exécuter en premier.  Si plusieurs threads de priorité identique sont tous disponibles, le planificateur parcourt les threads possédant cette priorité et attribue à chaque thread une tranche de temps fixe dans laquelle s'exécuter.  Tant qu'un thread de priorité supérieure est disponible pour l'exécution, les threads de priorité inférieure ne s'exécutent pas.  Lorsqu'il ne reste plus de threads exécutables possédant la même priorité, le planificateur passe à la priorité inférieure suivante et planifie l'exécution des threads de cette priorité.  Si un thread d'une priorité supérieure est exécutable, le thread de priorité inférieure prévaut et le thread de priorité supérieure est autorisé à s'exécuter de nouveau.  À tout cela s'ajoute le fait que le système d'exploitation peut également ajuster les priorités des threads dynamiquement tandis que l'interface utilisateur d'une application évolue entre le premier plan et l'arrière\-plan.  D'autres systèmes d'exploitation peuvent choisir d'utiliser un algorithme de planification différent.  
  
## Voir aussi  
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)   
 [Managed and Unmanaged Threading in Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)