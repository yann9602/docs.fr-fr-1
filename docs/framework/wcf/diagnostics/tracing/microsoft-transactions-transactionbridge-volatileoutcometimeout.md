---
title: "Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Le service du protocole WS\-AT a dépassé le délai spécifié lors de l'attente d'une réponse à un message de résultat provenant d'un participant volatil.Le résultat de la transaction peut s'avérer incertain si le participant retourne.  
  
## Description  
 Suivi lorsqu'un participant volatil a décidé de valider ou d'abandonner mais n'a pas répondu à une demande de validation ou de restauration dans un délai donné.  
  
## Résolution des problèmes  
 Assurez\-vous que tous les participants volatils sont en mesure de répondre dans le délai imparti.Le délai par défaut est de 180 secondes.S'il est insuffisant, augmentez le délai du minuteur `VolatileOutcomeDelay` de WS\-AT.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)