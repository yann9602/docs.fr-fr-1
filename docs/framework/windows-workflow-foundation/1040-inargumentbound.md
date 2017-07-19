---
title: "1040 - InArgumentBound | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1040 - InArgumentBound
## Propriétés  
  
|||  
|-|-|  
|ID|1040|  
|Mots clés|WFActivities|  
|Niveau|Verbose|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'un argument In a été trouvé.  
  
## Message  
 Dans l'argument « %1 » de l'activité « %2 », DisplayName : « %3 », InstanceId : « %4 » a été lié avec la valeur : %5.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|InArgument|xs:string|Nom de l'InArgument.|  
|Activité|xs:string|Nom de type de l'activité.|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|InstanceId|xs:string|ID d'instance de l'activité.|  
|Valeur|xs:string|Valeur liée à InArgument.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|