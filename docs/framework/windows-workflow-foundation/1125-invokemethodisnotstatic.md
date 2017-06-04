---
title: "1125 - InvokeMethodIsNotStatic | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1125 - InvokeMethodIsNotStatic
## Propriétés  
  
|||  
|-|-|  
|ID|1125|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Pendant l'étape CacheMetadata, l'activité InvokeMethod indique que la méthode à appeler n'est pas statique.  
  
## Message  
 InvokeMethod « %1 » \- la méthode n'est pas statique.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InvokeMethod|xs:string|Nom complet de l'activité InvokeMethod.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|