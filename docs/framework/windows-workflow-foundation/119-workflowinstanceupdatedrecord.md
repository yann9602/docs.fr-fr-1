---
title: "119 - WorkflowInstanceUpdatedRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 119 - WorkflowInstanceUpdatedRecord
## Propriétés  
  
|||  
|-|-|  
|ID|119|  
|Mots clés|HealthMonitoring, WFTracking|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow est mise à jour.  
  
## Message  
 TrackRecord\= WorkflowInstanceUpdatedRecord, InstanceID \= %1, RecordNumber \= %2, EventTime \= %3, ActivityDefinitionId \= %4, State \= %5, OriginalDefinitionIdentity \= %6, UpdatedDefinitionIdentity \= %7, Annotations \= %8, ProfileName \= %9  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|ActivityDefinitionId|xs:string|Nom de l'activité racine dans le workflow|  
|État|xs:string|État actuel du workflow.|  
|OriginalDefinitionIdentity|xs:string|ID de définition de workflow d'origine|  
|UpdatedDefinitionIdentity|xs:string|ID de définition mise à jour du workflow|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.  Les valeurs sont stockées dans un élément xml au format \<items\>\< item name \= "annotationName" type\="System.String"\>annotationValue\<\/item\>\<\/items\>.  Si aucune annotation n'est spécifiée, la chaîne contient \<items\/\>.  La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW.  Si la taille de l'événement dépasse les limites ETW, l'événement est tronqué en supprimant les annotations et en remplaçant la valeur d'annotation par \<items\>...\<\/items\>.|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|WorkflowDefinitionIdentity|xs:string|ID de flux de travail.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|