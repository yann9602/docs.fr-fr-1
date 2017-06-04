---
title: "Microsoft.Transactions.TransactionBridge.CommitMessageRetry | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.Transactions.TransactionBridge.CommitMessageRetry
Une nouvelle tentative de message de validation a été envoyée à un participant qui ne répond pas.  
  
## Description  
 Suivi lorsque le gestionnaire de transactions local a dû renvoyer un message de validation à un participant subalterne parce qu'il n'a pas reçu de réponse dans un délai donné.  
  
## Dépannage  
 Recherchez d'éventuels problèmes liés au réseau ou au produit pouvant empêcher la réponse d'être remise à temps.Si un nombre élevé de ces messages apparaissent, cela peut indiquer des problèmes d'infrastructure ou des délais de réponse anormalement longs.Ces deux problèmes réduiront considérablement le débit des transactions au sein du système.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)