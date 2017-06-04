---
title: "301 - UserDefinedErrorOccurred | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 301 - UserDefinedErrorOccurred
## Propriétés  
  
|||  
|-|-|  
|ID|301|  
|Mots clés|Dépannage, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Niveau|Erreur|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis à partir du code utilisateur.Les développeurs peuvent émettre cet événement lorsqu'une erreur personnalisée se produit dans leur service.Cela peut s'effectuer à l'aide des API <xref:System.Diagnostics.Eventing>.En outre, il existe un exemple WCF qui encapsule cette API et montre comment émettre correctement cet événement.  
  
## Message  
 Nom : '%1', Référence : '%2', Charge : %3  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Nom|`xs:string`|Nom de l'événement défini par l'utilisateur.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|Charge utile|`xs:string`|Charge utile de l'événement définie par l'utilisateur.|