---
title: "440 - StartSignpostEvent1 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 440 - StartSignpostEvent1
## Propriétés  
  
|||  
|-|-|  
|ID|440|  
|Mots clés|Dépannage|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Serveur d'applications \-Applications\/Analyse|  
  
## Description  
 Dans le suivi des activités, indique qu'un message a traversé une limite d'activité lors d'une opération d'envoi ou de réception.  
  
## Message  
 Limite d'activité.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|ExtendedData|`xs:string`|Nom de l'activité.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|