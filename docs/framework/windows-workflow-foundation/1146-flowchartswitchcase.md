---
title: "1146 - FlowchartSwitchCase | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 274e9209-1720-4512-a615-e742f00895f4
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1146 - FlowchartSwitchCase
## Propriétés  
  
|||  
|-|-|  
|ID|1146|  
|Mots clés|WFActivities|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique le cas sélectionné dans un commutateur Flowchart.  
  
## Message  
 Flowchart « %1 »\/FlowSwitch \- Le cas « %2 » a été sélectionné.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Organigramme|xs:string|Nom complet de l'organigramme.|  
|Case|xs:string|Le cas switch sélectionné.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|