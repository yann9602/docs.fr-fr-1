---
title: "Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
Le service du protocole WS\-AT a échoué l'envoi d'un message Register à son coordinateur  
  
## Description  
 Un suivi est effectué si le TransactionManager local n'est pas en mesure de s'inscrire auprès de son supérieur TransactionManager en raison de l'incapacité à envoyer un message.  
  
## Dépannage  
 Inspectez le message de suivi pour l'exception qui provoque l'échec de l'envoi du message.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)