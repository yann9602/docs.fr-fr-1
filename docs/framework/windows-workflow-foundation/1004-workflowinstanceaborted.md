---
title: "1004 - WorkflowInstanceAborted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 1004 - WorkflowInstanceAborted
## Propriétés  
  
|||  
|-|-|  
|ID|1004|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une instance de worfklow a été abandonnée avec une exception.  
  
## Message  
 ID WorkflowInstance : « %1 » a été abandonné avec une exception.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|ID d'instance pour le workflow|  
|Exception|`xs:string`|Détails de l'exception|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|