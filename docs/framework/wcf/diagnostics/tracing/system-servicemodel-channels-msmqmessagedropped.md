---
title: "System.ServiceModel.Channels.MsmqMessageDropped | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqMessageDropped
MSMQ a supprimé le message.  
  
## Description  
 Cette trace indique qu'un message MSMQ a été supprimé.Les messages MSMQ peuvent être supprimés lorsque [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] \(utilisé avec le NetMsmqBinding ou MsmqIntegrationBinding\) ne peut pas les traiter.Ces messages sont appelés des messages incohérents.  
  
 Un message incohérent est supprimé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Drop`.Ce message est supprimé de la file d'attente et ne peut plus être récupéré.  
  
 Consultez [Gestion de message incohérent](http://go.microsoft.com/fwlink/?LinkID=99546) \(page pouvant être en anglais\) pour plus d'informations sur le moment où les messages deviennent incohérents et sur la façon de configurer votre service pour les gérer convenablement.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [Gestion des messages empoisonnés](http://go.microsoft.com/fwlink/?LinkID=99546)