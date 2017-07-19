---
title: "System.ServiceModel.Channels.MsmqMessageRejected | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqMessageRejected
MSMQ a refusé le message.  
  
## Description  
 Ce suivi indique qu'un message MSMQ a été refusé.  
  
 Les messages MSMQ peuvent être refusés lorsque [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] \(utilisé avec NetMsmqBinding ou MsmqIntegrationBinding\) ne peut pas les traiter.Ces messages sont appelés des messages incohérents.Un message incohérent est refusé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`.Un message refusé est restitué à la [file d'attente des lettres mortes](http://go.microsoft.com/fwlink/?LinkID=99544) \(page pouvant être en anglais\) de l'expéditeur.  
  
 Consultez [Gestion des messages incohérents](http://go.microsoft.com/fwlink/?LinkID=99546) \(page pouvant être en anglais\) pour plus d'informations sur le moment où les messages deviennent incohérents et sur la façon de configurer votre service pour les gérer convenablement.  
  
 Consultez [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) \(page pouvant être en anglais\) pour plus d'informations sur ce que signifie un message refusé dans MSMQ.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [Gestion des messages empoisonnés](http://go.microsoft.com/fwlink/?LinkID=99546)   
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)