---
title: "Contention ETW Events | Microsoft Docs"
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
  - "contention events [.NET Framework]"
  - "ETW, contention events (CLR)"
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# Contention ETW Events
Les événements de conflit sont déclenchés chaque fois qu'il existe un conflit sur les verrous <xref:System.Threading.Monitor?displayProperty=fullName> ou les verrous natifs utilisés par le runtime.  Le conflit se produit lorsqu'un thread attend un verrou alors qu'un autre thread possède ce verrou.  
  
 Le tableau suivant montre le mot clé sous lequel les événements de conflit sont déclenchés, et le niveau des événements. \(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).\)  
  
|Mot clé destiné à déclencher l'événement.|Niveau|  
|-----------------------------------------------|------------|  
|`ContentionKeyword` \(0x4000\)|Informations \(4\)|  
  
 Le tableau suivant affiche des informations sur les événements.  
  
|Événement|ID d'événement|Déclenché lorsque|  
|---------------|--------------------|-----------------------|  
|`ContentionStart_V1`|81|Le conflit démarre.  Cet événement n'inclut pas le temps qui s'écoule avant qu'un thread ne commence à attendre pour l'acquisition d'un verrou. Il est déclenché uniquement lorsque l'attente commence.|  
|`ContentionStop`|81|Le conflit se termine.|  
  
 Le tableau suivant répertorie les données d'événement.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|Indicateurs|win:UInt8|0 pour managé ; 1 pour natif.|  
|ClrInstanceID|win:UInt16|ID unique pour l'instance de CLR.|  
  
## Voir aussi  
 [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md)