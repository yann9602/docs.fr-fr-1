---
title: "39458 - TrackingRecordTruncated | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 39458 - TrackingRecordTruncated
## Propriétés  
  
|||  
|-|-|  
|ID|39458|  
|Mots clés|WFTracking|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'un enregistrement de suivi a été tronqué.  Les données de variables\/annotations\/utilisateur ont été supprimées.  
  
## Message  
 Enregistrement de suivi %1 tronqué écrit dans la session ETW avec le fournisseur %2.  Les données de variables\/annotations\/utilisateur ont été supprimées  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|RecordNumber|xs:string|Numéro d'enregistrement de suivi.|  
|ProviderId|xs:string|ID du fournisseur ETW.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|