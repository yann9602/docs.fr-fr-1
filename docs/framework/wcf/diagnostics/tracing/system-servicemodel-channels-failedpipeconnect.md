---
title: "System.ServiceModel.Channels.FailedPipeConnect | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.FailedPipeConnect
Une tentative de connexion au point de terminaison du canal nommé a échoué.Une autre tentative est effectuée dans le délai d'attente spécifié.  
  
## Description  
 Ce suivi d'informations indique l'échec d'une connexion à un point de terminaison de canal nommé.Cela peut se produire si le point de terminaison de canal nommé est introuvable ou occupé.D'autres tentatives sont effectuées, chacune séparée par un bref lapse de temps jusqu'à ce que l'une réussisse ou que OpenTimeout expire.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)