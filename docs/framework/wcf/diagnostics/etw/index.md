---
title: "Analytic Tracing with ETW | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "diagnostics [WCF], analytic tracing"
  - "administration [WCF], analytic tracing"
  - "analytic tracing [WCF]"
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Analytic Tracing with ETW
Le traçage analytique [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] permet de capturer des informations de diagnostic lors de l'exécution d'un service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].Les événements du traçage analytique [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sont émis à des points clés dans la pile [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pour permettre de résoudre des problèmes liés aux services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dans un environnement de production.Le traçage analytique des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] a un impact minime sur les performances d'un serveur de produits hébergeant des services [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], car ces événements sont très efficacement émis vers une session du suivi d'événements Windows \(ETW\).  
  
## Dans cette section  
 [Vue d'ensemble du traçage analytique](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 Explique comment le traçage analytique [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] fonctionne avec [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Activation dynamique du traçage analytique](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 Explique comment activer ou désactiver le traçage de manière dynamique à l'aide d'ETW.  
  
 [Configuration du suivi de flux de messages](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 Décrit comment configurer le traçage du flux des messages.  
  
 [Référence d'événement de trace analytique](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 Affiche une table d'ID d'événements avec leurs niveaux d'événements, leurs messages d'événements et leurs mots clés.  
  
## Voir aussi  
 [WCF Services et suivi d'événements Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)   
 [Événements de suivi dans Event Tracing for Windows](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)