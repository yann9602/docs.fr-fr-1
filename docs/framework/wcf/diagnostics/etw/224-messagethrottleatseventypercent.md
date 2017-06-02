---
title: "224 - MessageThrottleAtSeventyPercent | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 224 - MessageThrottleAtSeventyPercent
## Propriétés  
  
|||  
|-|-|  
|ID|224|  
|Mots clés|EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 L'événement `MessageThrottleExceeded` est émis lorsque l'un des accélérateurs de service principaux a été dépassé.Cet événement est émis lorsque le pic d'activité diminue et que la valeur actuelle de l'accélérateur est de 70 % de la limitation actuellement définie.Notez que cet événement n'est émis que lorsque l'activité ralentit.Si la valeur actuelle tourne autour de 70 %, \(par exemple, 70,69,70,71,70,69\), seule la première occurrence de 70 % provoque un événement.Une fois cet événement émis, les prochains dépassements de la limitation définie pour l'accélérateur entraînent un événement `MessageThrottleExceeded`.  
  
## Message  
 La valeur de la limitation '%1' de '%2' est à 70%%.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Nom de l'accélérateur|`xs:string`|Nom de l'accélérateur qui a été dépassé.`MaxConcurrentCalls`, `MaxConcurrentInstances` ou  `MaxConcurrentSessions`.|  
|Limitation|`xs:long`|Limitation configurée actuellement pour l'accélérateur.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|