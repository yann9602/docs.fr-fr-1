---
title: "System.ServiceModel.Channels.ConnectionPoolCloseException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# System.ServiceModel.Channels.ConnectionPoolCloseException
Une exception s'est produite en fermant les connexions dans ce pool de connexions.  
  
## Description  
 Ce suivi de niveau d'erreur indique qu'une erreur s'est produite en fermant les pools de connexions utilisés par la fonctionnalité de mise en pool de connexions de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].L'une des raisons possibles est l'échec de la fermeture d'une connexion en groupe, ou d'un jeu de connexions en groupe, dans CloseTimeout.Lorsque cette exception est levée, toutes les connexions ouvertes restantes dans ce pool sont abandonnées ; les connexions ouvertes dans d'autres pools sont abandonnées.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)