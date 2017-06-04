---
title: "1036 - RuntimeTransactionCompletionRequested | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1036 - RuntimeTransactionCompletionRequested
## Propriétés  
  
|||  
|-|-|  
|ID|1036|  
|Mots clés|WFRuntime|  
|Niveau|Verbose|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une activité a planifié la fin de la transaction runtime.  
  
## Message  
 L'activité « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié la fin de la transaction runtime.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Activité|xs:string|Nom de type de l'activité.|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|InstanceId|xs:string|ID d'instance de l'activité.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|