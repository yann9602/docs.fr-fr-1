---
title: "217 - ClientOperationPrepared | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 217 - ClientOperationPrepared
## Propriétés  
  
|||  
|-|-|  
|ID|217|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis par des clients juste avant qu'une opération soit envoyée au service.  
  
## Message  
 Le client exécute l'action '%1' associée au contrat '%2'.Le message sera envoyé à '%3'.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Action|`xs:string`|En\-tête d'action SOAP du message sortant.|  
|Nom de contrat|`xs:string`|Nom du contrat.Exemple : ICalculator.|  
|Destination|`xs:string`|Adresse du point de terminaison de service auquel le message est envoyé.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|