---
title: "1124 - InvokeMethodIsStatic | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1124 - InvokeMethodIsStatic
## Propriétés  
  
|||  
|-|-|  
|ID|1124|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Pendant l'étape CacheMetadata, l'activité InvokeMethod indique que la méthode à appeler est statique.  
  
## Message  
 InvokeMethod « %1 » \- la méthode est statique.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InvokeMethod|xs:string|Nom complet de l'activité InvokeMethod.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|