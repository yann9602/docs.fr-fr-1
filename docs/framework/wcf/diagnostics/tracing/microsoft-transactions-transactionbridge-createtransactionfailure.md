---
title: "Microsoft.Transactions.TransactionBridge.CreateTransactionFailure | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
Une transaction n'a pas pu être créée.  
  
## Description  
 Ce suivi est généré lorsque MSDTC ne peut pas créer de transaction.  Cela peut être dû à des ressources faibles, un espace de journal insuffisant ou d'autres erreurs.  
  
## Résolution des problèmes  
 Inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)