---
title: "System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
La transaction spécifiée pour l'opération indiquée s'est terminée en raison d'un abandon asynchrone.  
  
## Description  
 La transaction courante a été abandonnée car un autre participant a voté Abort, le délai a été dépassé et une autre erreur s'est produite à l'intérieur du participant d'une transaction.  
  
## Résolution des problèmes  
 Si cet abandon est inattendu, vérifiez tous les journaux système afin de déterminer la véritable raison de l'abandon.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)