---
title: "39457 - TrackingRecordRaised | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a2731d1-c731-4b79-bb69-016cb69ef481
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 39457 - TrackingRecordRaised
## Propriétés  
  
|||  
|-|-|  
|ID|39457|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'un TrackingRecord a été déclenché dans un TrackingParticipant.  
  
## Message  
 Enregistrement suivi %1 élevé à %2.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|RecordNumber|xs:string|Numéro d'enregistrement de suivi.|  
|ParticipantId|xs:string|Participant de suivi.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|