---
title: "220 - MessageSentToTransport | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 220 - MessageSentToTransport
## Propriétés  
  
|||  
|-|-|  
|Id|220|  
|Mots clés|EndToEndMonitoring, Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis lorsque le modèle de service envoie un message au transport.  
  
> [!NOTE]
>  Il n'est pas émis pour les transports unidirectionnels.  
  
## Message  
 Le répartiteur a envoyé un message au transport.ID de corrélation \=\= '%1.'  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|ID de corrélation|`xs:GUID`|ID d'activité utilisé pour mettre en corrélation un événement `MessageSentToTransport` provenant d'un service ou d'un client avec son événement `MessageReceivedFromTransport` correspondant à l'autre bout.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|