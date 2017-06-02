---
title: "403 - SuspendSignpostEvent | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 403 - SuspendSignpostEvent
## Propriétés  
  
|||  
|-|-|  
|ID|403|  
|Mots clés|Résolution des problèmes|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Cet événement marque l'interruption d'une activité de bout en bout.  Il contient le nom de l'activité.  
  
## Message  
 Limite d'activité.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Données étendues|`xs:string`|Nom de l'activité.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|