---
title: Regroupement de messages mis en file d'attente dans une session
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
helpviewer_keywords: queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0dbd9d28d56d8d473b9e92d977da409b74290224
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-queued-messages-in-a-session"></a>Regroupement de messages mis en file d'attente dans une session
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit une session qui vous permet de regrouper un ensemble de messages connexes à traiter par une application de réception unique. Les messages qui font partie d'une session doivent faire partie de la même transaction. Étant donné que tous les messages font partie de la même transaction, si un message n'est pas traité, la session entière est restaurée. Les sessions ont des comportements semblables en ce qui concerne les files d'attente de lettres mortes et les files d'attente de messages incohérents. La propriété Durée de vie (Time to Live ou TTL) définie sur une liaison mise en file d'attente configurée pour les sessions est appliquée à la session dans son ensemble. Si seulement quelques-uns des messages de la session sont envoyés avant l'expiration de la durée de vie, la session entière est placée dans la file d'attente de lettres mortes. De même, lorsque les messages d'une session ne parviennent pas à être envoyés à une application depuis la file d'attente de l'application, la session entière est placée dans la file d'attente de messages incohérents (si disponible).  
  
## <a name="message-grouping-example"></a>Exemple de regroupement de messages  
 Le regroupement de messages peut être utile lors de l'implémentation d'une application de traitement de commandes en tant que service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Par exemple, un client soumet à cette application une commande qui contient plusieurs éléments. Pour chaque élément, le client passe un appel au service, ce qui provoque l'envoi d'un message séparé. Il est possible que le serveur A reçoive le premier élément et que le serveur B reçoive le deuxième élément. Chaque fois qu'un élément est ajouté, le serveur qui traite cet élément doit rechercher la commande appropriée et lui ajouter l'élément, ce qui est peu efficace. Vous rencontrez également de telles inefficacités avec un seul serveur gérant toutes les demandes, parce que le serveur doit faire le suivi de toutes les commandes en cours de traitement et déterminer à quelle commande le nouvel élément appartient. Le regroupement de toutes les demandes pour une commande unique simplifie grandement l'implémentation d'une telle application. L'application cliente envoie tous les éléments d'une commande unique dans une session, donc lorsque le service traite la commande, il traite la session entière en une fois. \  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Pour paramétrer un contrat de service pour qu'il utilise des sessions  
  
1.  Définissez un contrat de service qui requiert une session. Faites ceci avec l'attribut <xref:System.ServiceModel.OperationContractAttribute> et en spécifiant :  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  Marquez les opérations du contrat comme étant unidirectionnelles, parce que ces méthodes ne retournent rien. Faites ceci avec l'attribut <xref:System.ServiceModel.OperationContractAttribute> et en spécifiant :  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  Implémentez le contrat de service et spécifiez un `InstanceContextMode` de `PerSession`. Cela instancie le service une seule fois pour chaque session.  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  Chaque opération de service requiert une transaction. Spécifiez ceci avec l'attribut <xref:System.ServiceModel.OperationBehaviorAttribute>. L'opération qui complète la transaction doit également affecter à `TransactionAutoComplete` la valeur `true`.  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  Configurez un point de terminaison qui utilise la liaison `NetMsmqBinding` fournie par le système.  
  
6.  Créez une file d'attente transactionnelle en utilisant <xref:System.Messaging>. Vous pouvez également créer la file d'attente en utilisant Message Queuing (MSMQ) ou MMC. Dans ce cas, créez une file d'attente transactionnelle.  
  
7.  Créez un hôte de service pour le service en utilisant <xref:System.ServiceModel.ServiceHost>.  
  
8.  Ouvrez l'hôte de service pour rendre le service disponible.  
  
9. Fermez l'hôte de service.  
  
#### <a name="to-set-up-a-client"></a>Pour installer un client  
  
1.  Créez une étendue de transaction pour écrire dans la file d’attente transactionnelle.  
  
2.  Créer le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client à l’aide de la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil.  
  
3.  Passez la commande.  
  
4.  Fermez le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L'exemple suivant fournit le code pour le service `IProcessOrder` et pour un client qui utilise ce service. Il montre comment [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise des sessions mises en file d'attente pour fournir le comportement de regroupement.  
  
### <a name="code-for-the-service"></a>Code du service  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a>Code du client  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a>Voir aussi  
 [Files d’attente et sessions](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Vue d’ensemble des files d’attente](../../../../docs/framework/wcf/feature-details/queues-overview.md)
