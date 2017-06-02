---
title: "303 - UserDefinedInformationEventOccured | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 303 - UserDefinedInformationEventOccured
## Propriétés  
  
|||  
|-|-|  
|ID|303|  
|Mots clés|Dépannage, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis à partir du code utilisateur.Les développeurs peuvent émettre cet événement lorsqu'un événement d'informations personnalisé se produit dans leur service.Cela peut s'effectuer à l'aide des API <xref:System.Diagnostics.Eventing>.En outre, il existe un exemple WCF qui encapsule cette API et montre comment émettre correctement cet événement.  
  
## Message  
 Nom : '%1', Référence : '%2', Charge : %3  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Nom|`xs:string`|Nom de l'événement défini par l'utilisateur.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|Charge utile|`xs:string`|Charge utile de l'événement définie par l'utilisateur.|