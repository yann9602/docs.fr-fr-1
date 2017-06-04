---
title: "1032 - ScheduleRuntimeWorkItem | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1032 - ScheduleRuntimeWorkItem
## Propriétés  
  
|||  
|-|-|  
|ID|1032|  
|Mots clés|WFRuntime|  
|Niveau|Verbose|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'un RuntimeWorkItem a été planifié.  
  
## Message  
 Un élément de travail runtime a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Activité|xs:string|Nom de type de l'activité.|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|InstanceId|xs:string|ID d'instance de l'activité.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|