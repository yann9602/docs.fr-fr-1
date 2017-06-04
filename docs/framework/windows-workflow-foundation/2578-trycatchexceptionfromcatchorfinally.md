---
title: "2578 - TryCatchExceptionFromCatchOrFinally | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4803fee6-b8d8-4937-9907-d5c5fd5299db
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 2578 - TryCatchExceptionFromCatchOrFinally
## Propriétés  
  
|||  
|-|-|  
|ID|2578|  
|Mots clés|WFActivities|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une activité Catch ou Finally a levé une exception.  
  
## Message  
 Une activité Catch ou Finally associée à l'activité TryCatch « %1 » a levé une exception.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|