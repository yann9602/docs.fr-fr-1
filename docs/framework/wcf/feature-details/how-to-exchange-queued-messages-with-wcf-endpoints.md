---
title: "Comment&#160;: &#233;changer des messages en file d&#39;attente avec des points de terminaison WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# Comment&#160;: &#233;changer des messages en file d&#39;attente avec des points de terminaison WCF
Les files d'attente garantissent une messagerie fiable entre un client et un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], même si le service n'est pas disponible au moment de la communication. Les procédures ci-dessous indiquent comment garantir une communication durable entre un client et un service en utilisant la liaison mise en file d'attente standard lors de l'implémentation du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Cette section explique comment utiliser <xref:System.ServiceModel.NetMsmqBinding> pour la communication en file d’attente entre un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client et un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Pour utiliser la mise en file d'attente dans un service WCF  
  
1.  Définir un contrat de service à l’aide d’une interface marquée avec la <xref:System.ServiceModel.ServiceContractAttribute>. Marquez les opérations dans l’interface qui font partie du contrat de service avec le <xref:System.ServiceModel.OperationContractAttribute> et définissez-les comme unidirectionnelles car aucune réponse à la méthode est retournée. Le code ci-dessous fournit un exemple de contrat de service et sa définition d'opération.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  Lorsque le contrat de service passe des types définis par l'utilisateur, vous devez définir des contrats de données pour ces types. Le code suivant présente deux contrats de données, `PurchaseOrder` et `PurchaseOrderLineItem`. Ces deux types définissent les données qui sont envoyées au service. (Notez que les classes qui définissent ce contrat de données définissent également plusieurs méthodes. Ces méthodes ne sont pas considérées comme des parties intégrantes du contrat de données. Seuls les membres déclarés avec l'attribut `DataMember` font partie du contrat de données.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  Implémentez dans une classe les méthodes du contrat de service définies dans l'interface.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Notez que la <xref:System.ServiceModel.OperationBehaviorAttribute> placés sur le `SubmitPurchaseOrder` (méthode). Cela indique que cette opération doit être appelée au sein d’une transaction et que la transaction se termine automatiquement à la fin de la méthode.  
  
4.  Créer une file d’attente transactionnelle à l’aide de <xref:System.Messaging>. Vous pouvez éventuellement décider de créer la file d'attente à l'aide de la console MMC (Microsoft Management Console) MSMQ (Microsoft Message Queuing). Dans ce cas, assurez-vous de créer une file d’attente transactionnelle.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  Définir un <xref:System.ServiceModel.Description.ServiceEndpoint> de configuration qui spécifie l’adresse de service et utilise la norme <xref:System.ServiceModel.NetMsmqBinding> liaison. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]à l’aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration, consultez la page [configuration d’Applications Windows Communication Foundation](http://msdn.microsoft.com/fr-fr/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
  
  
6.  Créer un hôte pour le `OrderProcessing` à l’aide du service <xref:System.ServiceModel.ServiceHost> qui lit les messages de la file d’attente et les traite. Ouvrez l'hôte de service pour rendre le service disponible. Affichez un message qui indique à l'utilisateur d'appuyer sur une touche quelconque pour terminer le service. Appelez `ReadLine` pour attendre l'appui sur la touche, puis fermez le service.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Pour créer un client pour le service mis en file d'attente  
  
1.  L'exemple suivant montre comment exécuter l'application d'hébergement et utiliser l'outil Svcutil.exe pour créer le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  Définir un <xref:System.ServiceModel.Description.ServiceEndpoint> de configuration qui spécifie l’adresse et utilise la norme <xref:System.ServiceModel.NetMsmqBinding> de liaison, comme illustré dans l’exemple suivant.  
  
  
  
3.  Créez une étendue de transaction pour écrire dans la file d'attente transactionnelle, appelez l'opération `SubmitPurchaseOrder` et fermez le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], comme illustré dans l'exemple suivant.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent le code de service, l'application d'hébergement, le fichier App.config et le code client inclus pour cet exemple.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.NetMsmqBinding>   
 [Liaison MSMQ transactionnelles](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)   
 [Queuing dans WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)   
 [Comment : échanger des Messages avec des points de terminaison WCF et les Applications Message Queuing](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)   
 [Windows Communication Foundation pour Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)   
 [Installation de Message Queuing (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)   
 [Intégration Message Queuing exemples de liaisons](http://msdn.microsoft.com/fr-fr/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)   
 [Message Queuing à Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)   
 [Sécurité de message sur Message Queuing](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)