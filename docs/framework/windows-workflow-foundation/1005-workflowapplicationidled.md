---
title: "1005 - WorkflowApplicationIdled | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1005 - WorkflowApplicationIdled
## Propriétés  
  
|||  
|-|-|  
|ID|1005|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une application de workflow a été inactive.  
  
## Message  
 ID WorkflowApplication : « %1 » est devenu inactif.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|ID d'application de flux de travail|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|