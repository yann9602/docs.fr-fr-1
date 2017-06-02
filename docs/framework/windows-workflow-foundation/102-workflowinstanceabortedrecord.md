---
title: "102 - WorkflowInstanceAbortedRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bde4378d-4eea-4907-aaf2-c1a2bc770a37
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 102 - WorkflowInstanceAbortedRecord
## Propriétés  
  
|||  
|-|-|  
|Id|102|  
|Mots clés|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Serveur d'applications \-Applications\/Analyse|  
  
## Description  
 Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow émet un événement WorkflowInstanceAbortedRecord.  
  
## Message  
 TrackRecord \= WorkflowInstanceAbortedRecord, InstanceID \= %1, RecordNumber \= %2, EventTime \= %3, ActivityDefinitionId \= %4, Reason \= %5, Annotations \= %6, ProfileName \= %7  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|ActivityDefinitionId|xs:string|Nom de l'activité racine dans le workflow|  
|Reason|xs:string|Raison pour laquelle le workflow a été abandonné|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.Les valeurs sont stockées dans un élément xml au format \<items\>\< item  name \= "annotationName" type\="System.String"\>annotationValue\<\/item\>\<\/items\>.Si aucune annotation n'est spécifiée, la chaîne contient \<items\/\>.La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximum pour un événement ETW.Si la taille de l'événement dépasse les limites ETW, l'événement est tronqué en supprimant les annotations et en remplaçant la valeur d'annotation par \<items\>...\<\/items\>.|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName'. Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|