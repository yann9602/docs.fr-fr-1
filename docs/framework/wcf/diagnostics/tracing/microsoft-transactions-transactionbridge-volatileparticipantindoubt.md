---
title: "Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
Le service du protocole WS\-AT a reçu un message Prepared ou Replay d'un participant volatil non reconnu.Une faute a été renvoyée au participant, qui déclarera que le résultat de la transaction est douteux.  
  
## Description  
 Suivi généré lorsque le gestionnaire de transactions local reçoit un message Prepared ou Replay d'une inscription volatile qu'il a déjà oubliée.  
  
## Résolution des problèmes  
 Recherchez les causes potentielles de retard des messages qui viennent du participant volatil.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)