---
title: "1006 - WorkflowApplicationUnhandledException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1006 - WorkflowApplicationUnhandledException
## Propriétés  
  
|||  
|-|-|  
|ID|1006|  
|Mots clés|WFRuntime|  
|Niveau|Erreur|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une application de workflow a rencontré une exception non gérée.  
  
## Message  
 ID WorkflowInstance : « %1 » a rencontré une exception non prise en charge. L'exception provient de l'activité « %2 », DisplayName : « %3 ». L'action suivante sera effectuée : %4.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|ID d'instance pour le workflow|  
|Exception|`xs:string`|Détails de l'exception|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|