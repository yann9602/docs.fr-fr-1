---
title: "2576 - TryCatchExceptionFromTry | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47e48973-b17c-4a16-8338-c84b54aa0a6e
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 2576 - TryCatchExceptionFromTry
## Propriétés  
  
|||  
|-|-|  
|ID|2576|  
|Mots clés|WFActivities|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique que l'activité TryCatch a intercepté une exception.  
  
## Message  
 L'activité TryCatch « %1 » a intercepté une exception de type « %2 ».  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|Exception|xs:string|Nom de type de l'exception.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|