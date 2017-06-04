---
title: "1009 - ActivityScheduled | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1009 - ActivityScheduled
## Propriétés  
  
|||  
|-|-|  
|ID|1009|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une activité est planifiée en vue de son exécution.  
  
## Message  
 L'activité parent « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié l'activité enfant « %4 », DisplayName : « %5 », InstanceId : « %6 ».  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|ParentActivity|xs:string|Nom de type de l'activité parente.|  
|ParentDisplayName|xs:string|Nom complet de l'activité parente.|  
|ParentInstanceId|xs:string|ID d'instance de l'activité parente.|  
|ChildActivity|xs:string|Nom de type de l'activité enfant planifiée.|  
|ChildDisplayName|xs:string|Nom complet de l'activité enfant planifiée.|  
|ChildInstanceId|xs:string|ID d'instance de l'activité enfant planifiée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|