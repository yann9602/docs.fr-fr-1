---
title: "452 - MessageLogWarning | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22a9f6ea-5b5f-4110-8a4e-9be9c983fbbb
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 452 - MessageLogWarning
## Propriétés  
  
|||  
|-|-|  
|ID|452|  
|Mots clés|Dépannage, WCFMessageLogging|  
|Niveau|Avertissement|  
|Canal|Microsoft\-Windows\-Serveur d'applications \-Applications\/Analyse|  
  
## Description  
 Cet événement est émis lorsque l'avertissement du journal des messages est envoyé.  
  
## Message  
 %1  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|data1|`xs:string`||  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|