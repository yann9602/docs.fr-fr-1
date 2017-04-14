---
title: "3508 - TrackingProfileNotFound | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3508 - TrackingProfileNotFound
## Propriétés  
  
|||  
|-|-|  
|ID|3508|  
|Mots clés|WFServices|  
|Niveau|Verbose|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Indique si un TrackingProfile est introuvable dans le fichier de configuration ou un ActivityDefinitionId ne correspond pas au modèle.  
  
## Message  
 TrackingProfile « %1 » pour le ActivityDefinitionId « %2 » introuvable.  TrackingProfile est introuvable dans le fichier de configuration ou ActivityDefinitionId ne correspond pas.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|TrackingProfile|xs:string|Nom du modèle de suivi.|  
|ActivityDefinitionId|xs:string|ID de définition d'activité.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|