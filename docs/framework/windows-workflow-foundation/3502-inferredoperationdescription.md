---
title: "3502 - InferredOperationDescription | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3502 - InferredOperationDescription
## Propriétés  
  
|||  
|-|-|  
|ID|3502|  
|Mots clés|WFServices|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Indique qu'un OperationDescription a été déduit de WorkflowService.  
  
## Message  
 OperationDescription avec Name\='%1' dans le contrat « %2 » a été déduit de WorkflowService.  IsOneWay\=%3.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|OperationName|xs:string|Nom de l'opération.|  
|ContractName|xs:string|Nom du contrat.|  
|IsOneWay|xs:string|True ou False indiquant si le contrat est unidirectionnel.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|