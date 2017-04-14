---
title: "System.ServiceModel.TxFailedToNegotiateOleTx | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# System.ServiceModel.TxFailedToNegotiateOleTx
La négociation du protocole OleTransactions n'a pas pu se terminer pour le contexte de coordination spécifié.  
  
## Description  
 Tracé lorsqu'une transaction entrante avec des informations OleTx ne peut pas utiliser les informations OleTx jointes, et a recours à l'utilisation de WS\-AT à la place.  
  
## Résolution des problèmes  
 Indique un problème potentiel avec la communication de MSDTC RPC entre les ordinateurs.Si beaucoup de ces suivis apparaissent dans le journal, il peut s'ensuivre une baisse radicale des performances.Si OleTx n'est pas souhaité, affectez la valeur 0 à `OleTxUpgradeEnabled` dans la configuration du registre WS\-AT.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)