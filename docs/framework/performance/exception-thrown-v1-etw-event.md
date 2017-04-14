---
title: "Exception Thrown_V1 ETW Event | Microsoft Docs"
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
  - "ExceptionThrown_V1 event [.NET Framework]"
  - "ETW, ExceptionThrown_V1 event (CLR)"
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: 6
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 6
---
# Exception Thrown_V1 ETW Event
Cet événement capture des informations sur les exceptions levées.  
  
 Le tableau suivant affiche le mot clé sous lequel l'événement est déclenché, ainsi que le niveau de l'événement. \(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).\)  
  
|Mot clé destiné à déclencher l'événement.|Niveau|  
|-----------------------------------------------|------------|  
|`ExceptionKeyword` \(0x8000\)|Avertissement \(2\)|  
  
 Le tableau suivant affiche des informations sur les événements.  
  
|Événement|ID d'événement|Déclenché lorsque|  
|---------------|--------------------|-----------------------|  
|`ExceptionThrown_V1`|80|Une exception managée est levée.|  
  
 Le tableau suivant répertorie les données d'événement.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|Type d'exception|win:UnicodeString|Type de l'exception ; par exemple, `System.NullReferenceException`.|  
|Message d'exception|win:UnicodeString|Le message d'exception.|  
|EIPCodeThrow|win:Pointer|Pointeur d'instruction où l'exception s'est produite.|  
|ExceptionHR|win:UInt32|Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).|  
|ExceptionFlags|win:UInt16|0x01 : HasInnerException \(consultez [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) dans la documentation Visual Basic\).<br /><br /> 0x02 : IsNestedException.<br /><br /> 0x04 : IsRethrownException.<br /><br /> 0x08 : IsCorruptedStateException \(indique que l'état du processus est altéré ; consultez [Handling Corrupted State Exceptions \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179681) sur MSDN\).<br /><br /> 0x10 : IsCLSCompliant \(une exception qui dérive de <xref:System.Exception> est conforme CLS ; sinon elle n'est pas conforme CLS\).|  
|ClrInstanceID|win:UInt16|ID unique pour l'instance de CLR ou CoreCLR.|  
  
## Voir aussi  
 [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md)