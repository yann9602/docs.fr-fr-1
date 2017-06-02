---
title: "System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Impossible de déplacer ou de supprimer le message.  
  
## Description  
 Le suivi indique qu'un échec a eu lieu lors de la tentative de déplacement, d'élimination ou de rejet d'un message MSMQ.  
  
 Les messages MSMQ sont employés par [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] \(lorsque utilisé avec NetMsmqBinding ou MsmqIntegrationBinding\). Ce suivi concerne la valeur choisie pour la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding.  
  
 Ce suivi n'indique pas une défaillance générale du système.  Toutefois, il indique que la disposition de message incohérent choisie a échoué pour un message.  Consultez [Gestion des messages incohérents](http://go.microsoft.com/fwlink/?LinkID=99546) pour plus de détails sur le moment où les messages deviennent incohérents et comment configurer votre service pour les gérer de façon appropriée.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)