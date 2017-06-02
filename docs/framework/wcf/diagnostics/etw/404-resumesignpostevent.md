---
title: "404 - ResumeSignpostEvent | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 395cc7ca-f35f-4295-be97-39a077f99c97
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 404 - ResumeSignpostEvent
## Propriétés  
  
|||  
|-|-|  
|ID|404|  
|Mots clés|Dépannage|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications \-Applications\/Analyse|  
  
## Description  
 Cet événement marque la reprise d'une activité de bout en bout.Il contient le nom de l'activité.  
  
## Message  
 Limite d'activité.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Données étendues|`xs:string`|Nom de l'activité.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|