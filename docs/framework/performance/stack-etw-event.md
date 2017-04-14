---
title: "Stack ETW Event | Microsoft Docs"
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
  - "stack event [.NET Framework]"
  - "ETW, stack event (CLR)"
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# Stack ETW Event
L'événement de pile doit être utilisé conjointement à d'autres événements pour générer des traces de pile après le déclenchement d'un événement.  Il est journalisé lorsque le fournisseur de runtime est activé.  Il s'agit d'un événement très fréquent, car il est déclenché chaque fois qu'un autre événement de runtime est déclenché.  Pour cette raison, nous vous recommandons de l'utiliser avec précaution.  
  
 Le tableau suivant indique le mot clé et le niveau. \(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).\)  
  
|Mot clé destiné à déclencher l'événement.|Niveau|  
|-----------------------------------------------|------------|  
|`StackKeyword` \(0x40000000\)|Toujours journaliser \(0\)|  
  
 Le tableau suivant indique les informations d'événement.  
  
|Événement|ID d'événement|Déclenché lorsque|  
|---------------|--------------------|-----------------------|  
|`CLRStackWalk`|82|Conjointement à d'autres événements pour générer des traces de pile suite à un événement.|  
  
 Le tableau suivant répertorie les données d'événement.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|ClrInstanceID|win:Uint16|Identificateur d'exécution unique.|  
|Reserved1|win:UInt8|Réservé.|  
|Reserved2|win:UInt8|Réservé.|  
|FrameCount|win:UInt32|Nombre de frames dans la trace de la pile.|  
|Stack|win:Pointer|Colonnes de pointeurs d'instruction.|  
  
## Voir aussi  
 [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md)