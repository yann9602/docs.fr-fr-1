---
title: "&#201;v&#233;nements ETW dans la biblioth&#232;que parall&#232;le de t&#226;ches et PLINQ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tâches, événements ETW"
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# &#201;v&#233;nements ETW dans la biblioth&#232;que parall&#232;le de t&#226;ches et PLINQ
La bibliothèque parallèle de tâches et PLINQ génèrent les événements de suivi d'événements pour Windows \(ETW\) que vous pouvez utiliser pour profiler et dépanner des applications à l'aide d'outils tels que l'analyseur de performances Windows.  Toutefois, dans la plupart des scénarios, la meilleure méthode pour profiler du code d'application parallèle est d'utiliser le [Visualiseur concurrence](../Topic/Concurrency%20Visualizer.md) dans [!INCLUDE[vsUltShort](../../../includes/vsultshort-md.md)].  
  
## Événements ETW de la bibliothèque parallèle de tâches  
 Dans la structure EVENT\_HEADER, le ProviderId GUID pour les événements générés par <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=fullName> est :  
  
```  
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5  
```  
  
### Début de la boucle parallèle  
 EVENT\_DESCRIPTOR.Task \= 1  
  
 EVENT\_DESCRIPTOR.Id \= 1  
  
#### Données utilisateur  
  
|**Nom**|**Type**|**Description**|  
|-------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ID du TaskScheduler qui a démarré la boucle.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ID de la tâche qui a démarré la boucle.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|Identificateur unique utilisé pour indiquer l'imbrication et les paires pour les événements comportant des sémantiques de bifurcation\/jointure.|  
|OperationType|<xref:System.Int32?displayProperty=fullName>|Indique le type de boucle :<br /><br /> 1 \= ParallelInvoke<br /><br /> 2 \= ParallelFor<br /><br /> 3 \= ParallelForEach|  
|InclusiveFrom|<xref:System.Int64?displayProperty=fullName>|Valeur de départ du compteur de boucle|  
|ExclusiveTo|<xref:System.Int64?displayProperty=fullName>|Valeur finale du compteur de boucle.|  
  
### Fin de la boucle parallèle  
 EVENT\_DESCRIPTOR.Task \= 2  
  
 EVENT\_DESCRIPTOR.Id \= 2  
  
#### Données utilisateur  
  
|**Nom**|**Type**|**Description**|  
|-------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ID du TaskScheduler qui a démarré la boucle.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ID de la tâche qui a démarré la boucle.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|Identificateur unique utilisé pour indiquer l'imbrication et les paires pour les événements comportant des sémantiques de bifurcation\/jointure.|  
|totalIterations|<xref:System.Int64?displayProperty=fullName>|Nombre total d'itérations|  
  
### Début de l'appel parallèle  
 EVENT\_DESCRIPTOR.Task \= 3  
  
 EVENT\_DESCRIPTOR.Id \= 3  
  
#### Données utilisateur  
  
|**Nom**|**Type**|**Description**|  
|-------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ID du TaskScheduler qui a démarré la boucle.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ID de la tâche qui a démarré la boucle.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|Identificateur unique utilisé pour indiquer l'imbrication et les paires pour les événements comportant des sémantiques de bifurcation\/jointure.|  
|totalIterations|<xref:System.Int64?displayProperty=fullName>|Nombre total d'itérations|  
|operationType|<xref:System.Int32?displayProperty=fullName>|Indique le type de boucle :<br /><br /> 1 \= ParallelInvoke<br /><br /> 2 \= ParallelFor<br /><br /> 3 \= ParallelForEach|  
|ActionCount|<xref:System.Int32?displayProperty=fullName>|Nombre des actions qui seront exécutées dans l'appel parallèle.|  
  
### Fin de l'appel parallèle  
 EVENT\_DESCRIPTOR.Task \= 4  
  
 EVENT\_DESCRIPTOR.Id \= 4  
  
#### Données utilisateur  
  
|**Nom**|**Type**|**Description**|  
|-------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ID du TaskScheduler qui a démarré la boucle.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ID de la tâche qui a démarré la boucle.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|Identificateur unique utilisé pour indiquer l'imbrication et les paires pour les événements comportant des sémantiques de bifurcation\/jointure.|  
  
## Événements ETW PLINQ  
 L'EVENT\_HEADER.ProviderId GUID pour PLINQ est :  
  
```  
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87  
```  
  
### Début de requête parallèle  
 EVENT\_DESCRIPTOR.Task \= 1  
  
 EVENT\_DESCRIPTOR.Id \= 1  
  
#### Données utilisateur  
  
|**Nom**|**Type**|**Description**|  
|-------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ID du TaskScheduler qui a démarré la boucle.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ID de la tâche qui a démarré la boucle.|  
|QueryId|<xref:System.Int32?displayProperty=fullName>|Identificateur de requête unique.|  
  
### Fin de requête parallèle  
 EVENT\_DESCRIPTOR.Task \= 2  
  
 EVENT\_DESCRIPTOR.Id \= 2  
  
#### Données utilisateur  
  
|**Nom**|**Type**|**Description**|  
|-------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|ID du TaskScheduler qui a démarré la boucle.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|ID de la tâche qui a démarré la boucle.|  
|QueryId|<xref:System.Int32?displayProperty=fullName>|Identificateur de requête unique.|  
  
## Voir aussi  
 [ETW Events in the .NET Framework](../../../docs/framework/performance/etw-events.md)   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)