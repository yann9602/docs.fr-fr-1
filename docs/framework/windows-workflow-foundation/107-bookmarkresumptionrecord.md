---
title: "107--BookmarkResumptionRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa2d37ed-2bfa-439b-89e8-a9354027f155
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 107--BookmarkResumptionRecord
## Propriétés  
  
|||  
|-|-|  
|Id|107|  
|Mots clés|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications \-Applications\/Analyse|  
  
## Description  
 Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow émet un événement BookmarkResumptionRecord.  
  
## Message  
 TrackRecord \= BookmarkResumptionRecord, InstanceID\=%1, RecordNumber\=%2,EventTime\=%3, Name\=%4, SubInstanceID\=%5,  OwnerActivityName\=%6, OwnerActivityId \=%7, OwnerActivityInstanceId\=%8, OwnerActivityTypeName\=%9, Annotations\=%10, ProfileName \= %11  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|Name|xs:string|Nom du signet ayant été repris|  
|SubInstanceID|xs:GUID|ID de la portée de signet|  
|OwnerActivityName|xs:string|Nom de l'activité de signet|  
|OwnerActivityId|xs:string|ID de l'activité de signet|  
|OwnerActivityInstanceId|xs:string|ID d'instance de l'activité de signet|  
|OwnerActivityTypeName|xs:string|Type de l'activité de signet|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.Les valeurs sont stockées dans un élément xml au format \<items\>\< item  name \= "annotationName" type\="System.String"\>annotationValue\<\/item\>\<\/items\>.Si aucune annotation n'est spécifiée, la chaîne contient \<items\/\>.La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximum pour un événement ETW.Si la taille de l'événement dépasse les limites ETW, l'événement est tronqué en supprimant les annotations et en remplaçant la valeur d'annotation par \<items\>...\<\/items\>.|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName'. Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|