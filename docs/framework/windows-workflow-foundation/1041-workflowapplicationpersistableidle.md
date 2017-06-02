---
title: "1041 - WorkflowApplicationPersistableIdle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1041 - WorkflowApplicationPersistableIdle
## Propriétés  
  
|||  
|-|-|  
|ID|1041|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une application de workflow est inactive et persistante.  L'application de workflow sera inactive ou persistante.  
  
## Message  
 ID WorkflowApplication : « %1 » est inactif et persistant. L'action suivante sera effectuée : %2.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|WorkflowApplicationId|xs:string|ID d'application de flux de travail|  
|ActionTaken|xs:string|Mesure qui sera prise sur l'application de workflow.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|