---
title: "3503 - DuplicateCorrelationQuery | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3503 - DuplicateCorrelationQuery
## Propriétés  
  
|||  
|-|-|  
|ID|3503|  
|Mots clés|WFServices|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Indique qu'un CorrelationQuery en double a été trouvé.  Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.  
  
## Message  
 CorrelationQuery en double trouvé avec Where\='%1'.  Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Où|xs:string|Partie Where de la requête de corrélation.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|