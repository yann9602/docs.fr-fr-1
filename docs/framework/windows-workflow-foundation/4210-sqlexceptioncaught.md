---
title: "4210 - SqlExceptionCaught | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4210 - SqlExceptionCaught
## Propriétés  
  
|||  
|-|-|  
|ID|4210|  
|Mots clés|WFInstanceStore|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une exception SQL a été interceptée.  
  
## Message  
 Message %2 avec numéro d'exception SQL %1 intercepté.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|ErrorNumber|xs:string|Numéro d'erreur SQL.|  
|ExceptionMessage|xs:string|Message de l'exception SQL.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|