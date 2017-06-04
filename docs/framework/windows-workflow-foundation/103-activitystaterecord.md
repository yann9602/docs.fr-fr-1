---
title: "103 - ActivityStateRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 103 - ActivityStateRecord
## Propriétés  
  
|||  
|-|-|  
|ID|103|  
|Mots clés|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications \-Applications\/Analyse|  
  
## Description  
 Cet événement est émis par le participant de suivi ETW lorsqu'une activité dans une instance de workflow émet un événement ActivityStateRecord.  
  
## Message  
 TrackRecord \= ActivityStateRecord, InstanceID \=% 1, RecordNumber\=%2, EventTime\=%3, état \=% 4, Name\=%5, ActivityId\=%6, ActivityInstanceId\=%7, ActivityTypeName\=%8, Arguments\=%9, Variables\=%10, Annotations\=%11, ProfileName \=% 12  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|État|xs:string|État de l'activité.|  
|Nom|xs:string|Nom de l'activité qui a émis l'événement|  
|ActivityId|xs:string|ID d'activité de l'activité émettrice|  
|ActivityInstanceId|xs:string|ID d'instance de l'activité de l'activité émettrice|  
|ActivityTypeName|xs:string|Nom de type de l'activité émettrice|  
|Arguments|xs:string|Arguments suivis avec cet événement.Les valeurs sont stockées dans un élément xml au format \<éléments\>\< nom d'élément \= "argumentName" type\="System.String"\>argumentValue\<\/item\>\<\/items\>.Si aucun argument n'a été suivi, la chaîne contient \<items\/\>.La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW.Si la taille de l'événement dépasse les limites ETW, l'événement est tronqué en supprimant les annotations et en remplaçant la valeur d'annotation par \<items\>...\<\/items\>.Les types suivants sont stockés en tant que valeur telle que retournée par ToString\(\); string,char,bool,int,short,long,uint,ushort,ulong,System.Single,float,double,System.Guid,System.DateTimeOffset,System.DateTime.Tous les autres types sont sérialisés à l'aide de System.Runtime.Serialization.NetDataContractSerializer.|  
|Variables|xs:string|Les variables suivies avec cet événement.Les valeurs sont stockées dans un élément xml au format \<éléments\>\< nom d'élément \= "variableName" type\="System.String"\>variableValue\<\/item\>\<\/items\>.Si aucune variable n'a été suivie, la chaîne contient \<items\/\>.La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW.Si la taille de l'événement dépasse les limites ETW, l'événement est tronqué en supprimant les annotations et en remplaçant la valeur des variables par \<items\>...\<\/items\>.Les types suivants sont stockés en tant que valeur telle que retournée par ToString\(\); string,char,bool,int,short,long,uint,ushort,ulong,System.Single,float,double,System.Guid,System.DateTimeOffset,System.DateTime.Tous les autres types sont sérialisés à l'aide de System.Runtime.Serialization.NetDataContractSerializer.|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.Les valeurs sont stockées dans un élément xml au format \<items\>\< item  name \= "annotationName" type\="System.String"\>annotationValue\<\/item\>\<\/items\>.Si aucune annotation n'est spécifiée, la chaîne contient \<items\/\>.La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximum pour un événement ETW.Si la taille de l'événement dépasse les limites ETW, l'événement est tronqué en supprimant les annotations et en remplaçant la valeur d'annotation par \<items\>...\<\/items\>.|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName'. Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|