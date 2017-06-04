---
title: "218 - ClientOperationCompleted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 218 - ClientOperationCompleted
## Propriétés  
  
|||  
|-|-|  
|ID|218|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis par les clients juste après la fin d'une opération.Dans le cas des opérations monodirectionnelles, il est émis juste après l'envoi réussi du message.Dans le cas des opérations demande\-réponse, il est émis juste après la réception de la réponse.  
  
## Message  
 Le client a terminé d'exécuter l'action '%1' associée au contrat '%2'.Le message a été envoyé à '%3'.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Action|xs:string|En\-tête d'action SOAP du message sortant.|  
|Nom de contrat|`xs:string`|Nom du contrat.Exemple : ICalculator.|  
|Destination|`xs:string`|Adresse du point de terminaison de service auquel le message a été envoyé.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|