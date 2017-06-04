---
title: "1001 - WorkflowApplicationCompleted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 1001 - WorkflowApplicationCompleted
## Propriétés  
  
|||  
|-|-|  
|ID|1001|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une application de workflow s'est terminée à l'état Closed.  
  
## Message  
 ID WorkflowInstance : « %1 » s'est terminé à l'état Closed.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|ID d'instance pour le workflow|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|