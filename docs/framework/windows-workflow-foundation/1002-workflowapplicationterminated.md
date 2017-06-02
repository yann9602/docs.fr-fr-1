---
title: "1002 - WorkflowApplicationTerminated | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 1002 - WorkflowApplicationTerminated
## Propriétés  
  
|||  
|-|-|  
|ID|1002|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une application de workflow s'est arrêtée en l'état Faulted avec une exception.  
  
## Message  
 Identificateur de WorkflowApplication : « %1 » a été arrêté.  Il s'est terminé dans l'état Faulted avec une exception.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|ID d'application de flux de travail|  
|Exception|`xs:string`|Détails de l'exception|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|