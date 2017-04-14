---
title: "104 - ActivityScheduledRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae202178-8fb1-4646-a3aa-18beeda8ff93
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 104 - ActivityScheduledRecord
## Propriétés  
  
|||  
|-|-|  
|Id|104|  
|Mots clés|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications \-Applications\/Analyse|  
  
## Description  
 Cet événement est émis par le participant de suivi ETW lorsqu'une activité dans une instance de workflow émet un événement ActivityScheduledRecord.  
  
## Message  
 TrackRecord \= ActivityScheduledRecord, InstanceID \= %1,  RecordNumber \= %2, EventTime \= %3, Name \= %4, ActivityId \= %5, ActivityInstanceId \= %6, ActivityTypeName \= %7, ChildActivityName \= %8, ChildActivityId \= %9, ChildActivityInstanceId \= %10, ChildActivityTypeName \=%11, Annotations\=%12, ProfileName \= %13  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|Name|xs:string|Nom de l'activité ayant planifié l'activité enfant|  
|ActivityId|xs:string|ID de l'activité ayant planifié l'activité enfant|  
|ActivityInstanceId|xs:string|ID d'instance de l'activité ayant planifié l'activité enfant|  
|ActivityTypeName|xs:string|Type de l'activité qui a demandé l'opération d'annulation|  
|ChildActivityName|xs:string|Nom de l'activité planifiée|  
|ChildActivityId|xs:string|ID de l'activité planifiée|  
|ChildActivityInstanceId|xs:string|ID d'instance de l'activité planifiée|  
|ChildActivityTypeName|xs:string|Type de l'activité planifiée|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.Les valeurs sont stockées dans un élément xml au format \<items\>\< item  name \= "annotationName" type\="System.String"\>annotationValue\<\/item\>\<\/items\>.Si aucune annotation n'est spécifiée, la chaîne contient \<items\/\>.La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximum pour un événement ETW.Si la taille de l'événement dépasse les limites ETW, l'événement est tronqué en supprimant les annotations et en remplaçant la valeur d'annotation par \<items\>...\<\/items\>.|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName'. Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|