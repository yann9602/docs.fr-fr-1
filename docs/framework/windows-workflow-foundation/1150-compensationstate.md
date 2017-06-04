---
title: "1150 - CompensationState | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1150 - CompensationState
## Propriétés  
  
|||  
|-|-|  
|ID|1150|  
|Mots clés|WFActivities|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique un changement d'état d'un CompensableActivity.  
  
## Message  
 CompensableActivity « %1 » est dans l'état « %2 ».  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|État|xs:string|État de compensation.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|