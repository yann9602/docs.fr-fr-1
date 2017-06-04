---
title: "1103 - WorkflowActivitySuspend | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1103 - WorkflowActivitySuspend
## Propriétés  
  
|||  
|-|-|  
|ID|1103|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une activité du flux de travail a été interrompue.  
  
## Message  
 ID WorkflowInstance : « %1 » Activité E2E  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|WorkflowInstanceId|xs:string|ID de l'instance de flux de travail.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|