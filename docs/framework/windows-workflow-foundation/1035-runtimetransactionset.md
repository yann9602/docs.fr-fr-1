---
title: "1035 - RuntimeTransactionSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1035 - RuntimeTransactionSet
## Propriétés  
  
|||  
|-|-|  
|ID|1035|  
|Mots clés|WFRuntime|  
|Niveau|Verbose|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une activité a défini la transaction d'exécution.  
  
## Message  
 La transaction runtime a été définie par l'activité : « %1 », DisplayName : « %2 », InstanceID : « %3 ». Exécution isolée à l'activité « %4 », DisplayName : « %5 », InstanceID : « %6 ».  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Activité|xs:string|Nom de type de l'activité.|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|InstanceId|xs:string|ID d'instance de l'activité.|  
|IsolatedActivity|xs:string|Nom de type de l'activité dans laquelle la transaction est isolée.|  
|IsolatedActivityDisplayName|xs:string|Nom complet de l'activité dans laquelle la transaction est isolée.|  
|IsolatedActivityInstanceId|xs:string|ID d'instance de l'activité dans laquelle la transaction est isolée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|