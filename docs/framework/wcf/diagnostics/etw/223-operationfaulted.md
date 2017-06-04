---
title: "223 - OperationFaulted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 223 - OperationFaulted
## Propriétés  
  
|||  
|-|-|  
|ID|223|  
|Mots clés|EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis lorsque l'`OperationInvoker` par défaut du modèle de service a rencontré une exception dérivée de `FaultException` en appelant sa méthode.  
  
## Message  
 La méthode '%1' a levé un FaultException lors de l'appel effectué par l'OperationInvoker.Durée de l'appel de méthode : '%2' ms.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|MethodName|`xs:string`|Nom CLR de la méthode qui a été appelée par l'`OperationInvoker`.|  
|Durée|`xs:long`|Durée, en millisecondes, prise par l'`OperationInvoker` pour appeler la méthode.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|