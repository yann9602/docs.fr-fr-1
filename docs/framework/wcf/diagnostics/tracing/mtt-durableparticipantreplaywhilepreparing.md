---
title: "Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Le service de protocole WS\-AT a reçu un message Replay d'un participant durable n'ayant pas répondu au message Prepared.Par conséquent, la transaction a été abandonnée.  
  
## Description  
 Un suivi est généré si un message Replay est reçu lorsqu'un participant durable est encore en cours de préparation.Il s'agit d'un message illégal pour cet état et la transaction va être abandonnée.  
  
## Résolution des problèmes  
 Recevoir ce message d'erreur peut indiquer que la défaillance du participant durable \(notamment d'un gestionnaire de transactions subalterne\) est à présent résolue. Cependant, le résultat de la transaction étant incertain, une requête de statut est envoyée.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)