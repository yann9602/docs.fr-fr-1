---
title: "216 - MessageSentByTransport | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 216 - MessageSentByTransport
## Propriétés  
  
|||  
|-|-|  
|ID|216|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement se produit lorsqu'un transport basé sur TCP envoie un message.Notez qu'au niveau du transport, plusieurs messages peuvent être échangés entre clients et services pour une seule opération.Cela peut être dû au comportement d'infrastructure, la sécurité étant un bon exemple.Par conséquent, le nombre d'événements **MessageSentByTransport** émis varie en fonction de la liaison de votre service et de sa configuration.  
  
## Message  
 Le transport a envoyé un message à '%1.'  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|DestinationAddress|`xs:string`|Adresse à laquelle le message de demande a été envoyé.|  
|HostReference|xs:string|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|