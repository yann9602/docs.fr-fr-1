---
title: "Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
Le service du protocole WS\-AT a échoué l'enrôlement sur une transaction en utilisant le contexte de coordination fourni.  
  
## Description  
 Suivi lorsque MSDTC ne peut pas enrôler sur une transaction pour un protocole 2PC donné.Cela peut être dû au fait que la transaction n'existe plus, que l'enrôlement n'est plus autorisé, ou qu'un trop grand nombre d'enrôlements sont déjà présents.  
  
## Résolution des problèmes  
 Inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)