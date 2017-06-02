---
title: "105 - FaultPropagationRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 105 - FaultPropagationRecord
## Propriétés  
  
|||  
|-|-|  
|ID|105|  
|Mots clés|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Serveur d'applications \-Applications\/Analyse|  
  
## Description  
 Le participant au suivi ETW émet cet événement lorsqu'une activité dans l'instance de workflow émet FaultPropagationRecord.  
  
## Message  
 TrackRecord \= FaultPropagationRecord, InstanceID\=%1, RecordNumber\=%2, EventTime\=%3, FaultSourceActivityName\=%4, FaultSourceActivityId\=%5, FaultSourceActivityInstanceId\=%6, FaultSourceActivityTypeName\=%7, FaultHandlerActivityName\=%8, FaultHandlerActivityId \=% 9, FaultHandlerActivityInstanceId \=% 10, FaultHandlerActivityTypeName\=%11, Fault\=%12, IsFaultSource\=%13, Annotations\=%14, ProfileName \=% 15  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|FaultSourceActivityName|xs:string|Nom de l'activité qui a émis l'erreur|  
|FaultSourceActivityId|xs:string|ID de l'activité qui a émis l'erreur|  
|FaultSourceActivityInstanceId|xs:string|ID d'instance de l'activité qui a émis l'erreur|  
|FaultSourceActivityTypeName|xs:string|Type de l'activité qui a émis l'erreur|  
|FaultHandlerActivityName|xs:string|Nom complet de l'activité de gestionnaire d'erreur|  
|FaultHandlerActivityId|xs:string|ID de l'activité de gestionnaire d'erreur|  
|FaultHandlerActivityInstanceId|xs:string|ID d'instance de l'activité de gestionnaire d'erreur|  
|FaultHandlerActivityTypeName|xs:string|Type de l'activité de gestionnaire d'erreur|  
|Fault|xs:string|Détails d'erreur|  
|IsFaultSource|xs:unsignedByte|Indique si l'événement a été émis depuis la source ayant généré l'erreur|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.Les valeurs sont stockées dans un élément xml au format \<items\>\< item  name \= "annotationName" type\="System.String"\>annotationValue\<\/item\>\<\/items\>.Si aucune annotation n'est spécifiée, la chaîne contient \<items\/\>.La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximum pour un événement ETW.Si la taille de l'événement dépasse les limites ETW, l'événement est tronqué en supprimant les annotations et en remplaçant la valeur d'annotation par \<items\>...\<\/items\>.|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName'. Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|