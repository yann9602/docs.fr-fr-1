---
title: "215 - MessageReceivedByTransport | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 215 - MessageReceivedByTransport
## Propriétés  
  
|||  
|-|-|  
|ID|215|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Cet événement se produit lorsqu'un transport basé sur TCP reçoit un message.  Notez qu'au niveau du transport, plusieurs messages peuvent être échangés entre clients et services pour une seule opération.  Cela peut être dû au comportement d'infrastructure, la sécurité étant un bon exemple.  Par conséquent, le nombre d'événements `MessageReceivedByTransport` émis varie en fonction de la liaison de votre service et de sa configuration.  
  
> [!NOTE]
>  Cet événement n'est pas émis pour les transports unidirectionnels.  
  
## Message  
 Le transport a reçu un message de '%1'.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Adresse d'écoute|`xs:string`|Adresse qui a reçu le message.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.  Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.  Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|