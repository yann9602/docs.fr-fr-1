---
title: "39456 - TrackingRecordDropped | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 39456 - TrackingRecordDropped
## Propriétés  
  
|||  
|-|-|  
|ID|39456|  
|Mots clés|WFTracking|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'un enregistrement de suivi a été supprimé, car sa taille dépasse la taille maximale autorisée par le fournisseur de session ETW.  
  
## Message  
 La taille de l'enregistrement de suivi %1 dépasse la valeur maximale autorisée par la session ETW pour le fournisseur %2  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Exception|xs:string|Détails de l'exception|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|