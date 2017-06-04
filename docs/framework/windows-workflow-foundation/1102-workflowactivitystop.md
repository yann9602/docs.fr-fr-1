---
title: "1102 - WorkflowActivityStop | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 285e5cb8-e90d-4914-ac06-e9b176ffefa2
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1102 - WorkflowActivityStop
## Propriétés  
  
|||  
|-|-|  
|ID|1102|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une activité du flux de travail s'est arrêtée.  
  
## Message  
 ID WorkflowInstance : « %1 » Activité E2E  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|WorkflowInstanceId|xs:string|ID de l'instance de flux de travail.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|