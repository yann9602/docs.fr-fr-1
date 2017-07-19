---
title: "Services (Windows Workflow) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 521cdb66-98cb-4ad1-b706-370788a43485
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Services (Windows Workflow)
Cette section contient des exemples qui illustrent des scénarios qui utilisent des services de workflow.  
  
## Dans cette section  
 [OperationScope](../../../../docs/framework/windows-workflow-foundation/samples/operationscope.md)  
 Montre comment les activités de messagerie, <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>, peuvent être utilisées pour exposer une activité personnalisée existante en tant qu'opération dans un service de workflow.  
  
 [Accès à OperationContext](../../../../docs/framework/windows-workflow-foundation/samples/accessing-operationcontext.md)  
 Montre comment les activités de messagerie \(<xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.Send>\) peuvent être utilisées avec une activité de portée personnalisée pour accéder à <xref:System.ServiceModel.OperationContext.Current%2A> et attacher ou récupérer un en\-tête de message personnalisé dans un message sortant ou entrant.  
  
 [Corrélation de requête de message LINQ](../../../../docs/framework/windows-workflow-foundation/samples/linq-message-query-correlation.md)  
 Montre comment effectuer une corrélation basée sur le contenu à l'aide d'une implémentation <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisée par opposition au <xref:System.ServiceModel.XPathMessageQuery> fourni par le système.  
  
 [Calculatrice corrélée](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)  
 Montre comment utiliser les activités de messagerie \(<xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>\) dans le concepteur avec une corrélation basée sur le contenu selon un paramètre dans le message.  
  
 [Sécurisation des services de workflow](../../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md)  
 Montre la création d'un service de workflow de base à l'aide des activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>, et à l'aide de la configuration [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour définir des points de terminaison sécurisés à utiliser par le service de workflow.  
  
 [Communication asynchrone](../../../../docs/framework/windows-workflow-foundation/samples/asynchronous-communication.md)  
 Montre comment la communication entre deux services [!INCLUDE[wf](../../../../includes/wf-md.md)] différents s'effectue de façon asynchrone par défaut.