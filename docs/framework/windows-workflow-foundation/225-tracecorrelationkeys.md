---
title: "225 - TraceCorrelationKeys | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 225 - TraceCorrelationKeys
## Propriétés  
  
|||  
|-|-|  
|ID|225|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications\-Applications\/Analyse|  
  
## Description  
 Cet événement est émis lorsque la corrélation basée sur le contenu est utilisée pour un service de workflow.Il contient les clés de corrélation appliquées pour mettre en corrélation un message avec une instance.  
  
## Message  
 Clé de corrélation '%1' calculée à l'aide des valeurs '%2' dans l'étendue parente '%3'.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Clé d'instance|`xs:GUID`|Clé générée à partir des valeurs de corrélation.|  
|Valeurs|`xs:string`|Valeurs utilisées pour calculer la clé d'instance de corrélation.|  
|Étendue parente|`xs:string`||  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.Son format est défini de la façon suivante : 'Chemin d'accès virtuel de l'Application Nom du site Web&#124;Chemin d'accès virtuel du Service&#124;ServiceName.Exemple : 'Site Web par défaut\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|