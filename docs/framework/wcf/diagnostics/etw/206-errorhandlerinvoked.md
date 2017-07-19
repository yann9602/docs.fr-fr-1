---
title: "206 - ErrorHandlerInvoked | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 206 - ErrorHandlerInvoked
## Propriétés  
  
|||  
|-|-|  
|ID|206|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis une fois qu'un `ErrorHandler` a eu la possibilité de gérer une exception produite dans une opération de service.  
  
## Message  
 Le répartiteur a appelé un ErrorHandler de type '%1' avec une exception de type '%3.'ErrorHandled \=\= '%2.'  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|TypeName|`xs:string`|CLR FullName du type d'`ErrorHandler` appelé.|  
|Géré|`xs:unsignedByte`|`true` si le gestionnaire d'erreurs a géré l'erreur, sinon `false`.|  
|ExceptionTypeName|`xs:string`|CLR FullName de l'exception gérée.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|