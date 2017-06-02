---
title: "3552 - MaxPendingMessagesPerChannelExceeded | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 3552 - MaxPendingMessagesPerChannelExceeded
## Propriétés  
  
|||  
|-|-|  
|ID|3552|  
|Mots clés|Quota, WFServices|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Indique que la limitation « MaxPendingMessagesPerChannel » a été atteinte.  
  
## Message  
 La limitation « MaxPendingMessagesPerChannel » de « %1 » a été atteinte.  Pour accroître cette limite, modifiez la propriété MaxPendingMessagesPerChannel sur BufferedReceiveServiceBehavior.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Limitation|xs:string|La limite de MaxPendingMessagesPerChannel.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|