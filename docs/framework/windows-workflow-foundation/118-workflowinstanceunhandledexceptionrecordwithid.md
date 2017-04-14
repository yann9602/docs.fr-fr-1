---
title: "118 - WorkflowInstanceUnhandledExceptionRecordWithId | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 118 - WorkflowInstanceUnhandledExceptionRecordWithId
## Propriétés  
  
|||  
|-|-|  
|ID|118|  
|Mots clés|HealthMonitoring, WFTracking|  
|Niveau|Erreur|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow émet un événement WorkflowInstanceUnhandledExceptionRecord.  
  
## Message  
 TrackRecord \= WorkflowInstanceUnhandledExceptionRecord, InstanceID \= %1, RecordNumber \= %2, EventTime \= %3, ActivityDefinitionId \= %4, SourceName \= %5, SourceId \= %6, SourceInstanceId \= %7, SourceTypeName\=%8, Exception\=%9, Annotations\= %10, ProfileName \= %11, WorkflowDefinitionIdentity \= %12  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|ActivityDefinitionId|xs:string|Nom de l'activité racine dans le workflow|  
|SourceName|xs:string|Nom de l'activité source ayant généré l'erreur unhandledException|  
|SourceId|xs:string|ID d'activité de l'activité source ayant généré l'erreur|  
|SourceInstanceId|xs:string|ID d'instance de l'activité source ayant généré l'erreur|  
|SourceTypeName|xs:string|Nom du type de l'activité source ayant généré l'erreur unhandledException|  
|Exception|xs:string|Détails de l'exception non gérée|  
|État|xs:string|État actuel du workflow.|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.  Les valeurs sont stockées dans un élément xml au format \<items\>\< item name \= "annotationName" type\="System.String"\>annotationValue\<\/item\>\<\/items\>.  Si aucune annotation n'est spécifiée, la chaîne contient \<items\/\>.  La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW.  Si la taille de l'événement dépasse les limites ETW, l'événement est tronqué en supprimant les annotations et en remplaçant la valeur d'annotation par \<items\>...\<\/items\>.|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|WorkflowDefinitionIdentity|xs:string|ID de flux de travail.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|