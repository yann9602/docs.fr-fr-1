---
title: "213 - ServiceHostStarted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 213 - ServiceHostStarted
## Propriétés  
  
|||  
|-|-|  
|ID|213|  
|Mots clés|EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceHost|  
|Niveau|LogAlways|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis lors du démarrage d'un hôte de service hébergé par le Web.Cela se produit en général lorsque le service est activé par un message.Cela peut également arriver si le service est configuré pour démarrer automatiquement.  
  
## Message  
 ServiceHost a démarré : '%1'.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Nom de type de service|`xs:string`|CLR FullName du type de l'implémentation de service.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|