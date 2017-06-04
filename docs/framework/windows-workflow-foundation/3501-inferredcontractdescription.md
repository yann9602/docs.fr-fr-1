---
title: "3501 - InferredContractDescription | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21a70849-4fc0-41d2-b9a4-db5aa2acdf1a
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3501 - InferredContractDescription
## Propriétés  
  
|||  
|-|-|  
|ID|3501|  
|Mots clés|WFServices|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Indique qu'un ContractDescription a été déduit de WorkflowService.  
  
## Message  
 ContractDescription avec Name\='%1' et Namespace\='%2' a été déduit de WorkflowService.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Nom|xs:string|Nom de ContractDescription.|  
|Espace de noms|xs:string|Espace de noms de ContractDescription.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|