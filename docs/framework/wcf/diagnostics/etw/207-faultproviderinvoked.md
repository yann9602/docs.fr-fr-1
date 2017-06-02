---
title: "207 - FaultProviderInvoked | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 207 - FaultProviderInvoked
## Propriétés  
  
|||  
|-|-|  
|ID|207|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis après qu'un `FaultProvider` a été appelé.  
  
## Message  
 Le répartiteur a appelé un FaultProvider de type '%1' avec une exception de type '%2.'  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|TypeName|`xs:string`|CLR FullName du type de `FaultProvider` appelé.|  
|ExceptionTypeName|`xs:string`|CLR FullName de l'exception que le `FaultProvider` a traitée.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.  Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.  Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|