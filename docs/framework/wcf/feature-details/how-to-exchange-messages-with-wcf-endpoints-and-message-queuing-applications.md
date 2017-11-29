---
title: "Comment : échanger des messages avec des points de terminaison WCF et des applications Message Queuing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d09b8e662b2876fa5d5c5246ea7e7a4998cde9ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Comment : échanger des messages avec des points de terminaison WCF et des applications Message Queuing
Vous pouvez intégrer des applications Message Queuing (MSMQ) existantes aux applications [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] en utilisant la liaison d'intégration MSMQ qui convertit les messages MSMQ en messages [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et vice versa. Cela vous permet d'appeler des applications réceptrices MSMQ depuis des clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ainsi que d'appeler les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] depuis des applications expéditrices MSMQ.  
  
 De cette section, nous vous expliquons comment utiliser <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pour les communications mises en file d'attente entre (1) un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et un service d'application MSMQ écrit à l'aide de System.Messaging et (2) un client d'application MSMQ et un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Pour un exemple complet qui montre comment appeler une application de récepteur MSMQ à partir un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, consultez le [Windows Communication Foundation à Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) exemple.  
  
 Pour un exemple complet qui montre comment appeler un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de service à partir d’un client MSMQ, consultez le [Message Queuing pour Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) exemple.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Pour créer un service WCF qui reçoit des messages depuis un client MSMQ  
  
1.  Configurez une interface qui définit le contrat de service pour le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui reçoit les messages mis en file d'attente depuis une application expéditrice MSMQ, comme le montre l'exemple de code suivant.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  Implémentez l'interface et appliquez l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> à la classe, comme le montre l'exemple de code suivant.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  Créez un fichier de configuration qui spécifie la liaison <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
  
  
4.  Instanciez un objet <xref:System.ServiceModel.ServiceHost> qui utilise la liaison configurée.  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Pour créer un client WCF qui envoie des messages à une application réceptrice MSMQ  
  
1.  Configurez une interface qui définit le contrat de service pour le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui envoie les messages mis en file d'attente au récepteur MSMQ, comme le montre l'exemple de code suivant.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  Définissez une classe de client que le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise pour appeler le récepteur MSMQ.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  Créez une configuration qui spécifie l’utilisation de la liaison MsmqIntegrationBinding.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  Créez une instance de la classe de client et appelez la méthode définie par le service qui reçoit le message.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des files d’attente](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Comment : Exchange en file d’attente de Messages avec des points de terminaison WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Windows Communication Foundation à Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Installation de Message Queuing (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Message Queuing à Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Sécurité de message sur Message Queuing](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
