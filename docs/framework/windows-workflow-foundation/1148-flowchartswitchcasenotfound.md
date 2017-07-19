---
title: "1148 - FlowchartSwitchCaseNotFound | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ee7fcee-e040-4306-968e-ed840a1cb00c
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1148 - FlowchartSwitchCaseNotFound
## Propriétés  
  
|||  
|-|-|  
|ID|1148|  
|Mots clés|WFActivities|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une correspondance de cas ou un cas par défaut est introuvable dans un organigramme.  L'exécution de Flowchart va se terminer.  
  
## Message  
 Flowchart « %1 »\/FlowSwitch \- impossible de trouver l'activité Case ou un cas par défaut correspondant au résultat de l'expression.  L'exécution de Flowchart va se terminer.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Organigramme|xs:string|Nom complet de l'organigramme.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|