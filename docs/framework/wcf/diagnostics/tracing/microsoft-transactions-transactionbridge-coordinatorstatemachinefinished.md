---
title: "Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
La machine à états pour un enrôlement de coordinateur est passée à l'état Finished.  
  
## Description  
 Suivi lorsque le gestionnaire de transactions local croit qu'un enrôlement de coordinateur supérieur a terminé le traitement 2PC.Le résultat peut être Committed, Aborted ou Forgotten.Suivi également lorsque le gestionnaire de transaction local vote ReadOnly pendant la préparation.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)