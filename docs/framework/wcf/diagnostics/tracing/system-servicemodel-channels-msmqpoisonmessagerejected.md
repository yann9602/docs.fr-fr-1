---
title: "System.ServiceModel.Channels.MsmqPoisonMessageRejected | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqPoisonMessageRejected
Message poison rejeté.  
  
## Description  
 Le suivi indique qu'un message poison a été rencontré et rejeté par la suite.Cela se produit seulement lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`.Un message rejeté est restitué à la [file d'attente de lettres mortes](http://go.microsoft.com/fwlink/?LinkId=99544) \(page pouvant être en anglais\) de l'expéditeur.  
  
 Consultez [Gestion de message incohérent](http://go.microsoft.com/fwlink/?LinkId=99546) pour plus d'informations sur le moment où les messages deviennent incohérents et sur la façon de configurer votre service pour les gérer convenablement.Consultez [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) \(page pouvant être en anglais\) pour plus d'informations sur ce que signifie un message rejeté dans MSMQ.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [Gestion des messages empoisonnés](http://go.microsoft.com/fwlink/?LinkId=99546)   
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)