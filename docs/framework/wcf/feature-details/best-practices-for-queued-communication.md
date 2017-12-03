---
title: Meilleures pratiques pour les communications mises en file d'attente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15de43cc83e92b781e44da703353bec98dbc2c6a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="best-practices-for-queued-communication"></a>Meilleures pratiques pour les communications mises en file d'attente
Cette rubrique fournit des méthodes recommandées pour les communications mises en file d'attente dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Les sections suivantes traitent des méthodes recommandées à partir d'un scénario.  
  
## <a name="fast-best-effort-queued-messaging"></a>Messagerie mise en file attente efficace et rapide  
 Pour les scénarios qui requièrent la séparation fournie par la messagerie en file d'attente et une messagerie performante avec des assurances de meilleur-effort, utilisez une file d'attente non transactionnelle et affectez à la propriété <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> la valeur `false`.  
  
 De plus, vous pouvez choisir de ne pas encourir le coût des écritures sur disque en affectant à la propriété <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> la valeur `false`.  
  
 La sécurité a des conséquences sur la performance. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Considérations relatives aux performances](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Messagerie mise en file d'attente fiable de bout en bout  
 Les sections suivantes décrivent des méthodes recommandées pour les scénarios qui requièrent une messagerie fiable de bout en bout.  
  
### <a name="basic-reliable-transfer"></a>Transfert fiable de base  
 Pour une fiabilité de bout en bout, affectez à la propriété <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> la valeur `true` pour garantir le transfert. La propriété <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> peut avoir la valeur `true` ou `false` selon vos spécifications (la valeur par défaut est `true`). En général, la propriété <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> a la valeur `true` dans le cadre de la fiabilité de bout en bout. Ce compromis est a une incidence sur la performance, mais rend le message durable afin qu'il ne soit pas perdu si un gestionnaire de files d'attente tombe en panne.  
  
### <a name="use-of-transactions"></a>Utilisation des transactions  
 Vous devez utiliser des transactions pour garantir la fiabilité de bout en bout. `ExactlyOnce` garantit seulement que les messages sont remis à la file d'attente cible. Pour vous assurer que le message est reçu, utilisez des transactions. Sans transactions, si le service tombe en panne, vous perdez le message en cours de livraison qui est en fait remis à l'application.  
  
### <a name="use-of-dead-letter-queues"></a>Utilisation des files d'attente de lettres mortes  
 Les files d'attente de lettres mortes vous permettre d'être averti si un message n'est pas remis à la file d'attente cible. Vous pouvez utiliser la file d'attente de lettres mortes fournie par le système ou une file d'attente de lettres mortes personnalisée. En général, il est préférable d'utiliser une file d'attente de lettres mortes personnalisée car elle vous permet d'envoyer des messages de lettres mortes d'une application à une file d'attente de lettres mortes unique. Sinon, tous les messages de lettres mortes qui se produisent pour toutes les applications qui s'exécutent sur le système sont remis à une file d'attente unique. Chaque application doit ensuite parcourir la file d'attente de lettres mortes pour rechercher les messages de lettres mortes qui sont pertinents pour cette application. Parfois, l'utilisation d'une file d'attente de lettres mortes personnalisée n'est pas possible, lors de l'utilisation de MSMQ 3.0. par exemple.  
  
 La désactivation des files d'attente de lettres mortes pour les communications fiables de bout en bout n'est pas recommandée.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Échecs lors du transfert de lettres mortes à l’aide de files d’attente pour traiter des messages](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Utilisation de la gestion des messages incohérents  
 La gestion des messages empoisonnés permet de reprendre le traitement des messages après une défaillance.  
  
 Lorsque vous utilisez la fonctionnalité de gestion des messages incohérents, vérifiez que la propriété <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> a la valeur appropriée. Lui affecter la valeur <xref:System.ServiceModel.ReceiveErrorHandling.Drop> signifie que les données sont perdues. En revanche, lui affecter la valeur <xref:System.ServiceModel.ReceiveErrorHandling.Fault> entraîne la défaillance de l'hôte de service lorsqu'il détecte un message incohérent. Avec MSMQ 3.0, <xref:System.ServiceModel.ReceiveErrorHandling.Fault> est la meilleure option pour éviter la perte de données et se débarrasser du message incohérent. Avec MSMQ 4.5, <xref:System.ServiceModel.ReceiveErrorHandling.Move> est l'approche recommandée. <xref:System.ServiceModel.ReceiveErrorHandling.Move> déplace un message incohérent hors de la file d'attente afin que le service puisse continuer à traiter de nouveaux messages. Le service des messages incohérents peut ensuite traiter séparément le message incohérent.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Gestion des messages incohérents](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Obtention d'un haut débit  
 Pour obtenir un débit supérieur sur un point de terminaison unique, utilisez les fonctionnalités suivantes :  
  
-   Traitement transactionnel par lots. Le traitement transactionnel par lots permet de lire de nombreux messages dans une transaction unique. Il optimise les validations de transactions et augmente la performance globale. L'inconvénient du traitement par lots est que si une défaillance se produit dans un message unique dans un lot, le lot entier est restauré et les messages doivent être traités un par un jusqu'à ce que le traitement par lots soit revenu sûr. Dans la plupart des cas, les messages incohérents sont rares, donc le traitement par lots est le meilleur moyen d’augmenter les performances du système, en particulier lorsque d’autres gestionnaires de ressources participent à la transaction. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Le traitement par lot des Messages dans une Transaction](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
-   Accès concurrentiel. L'accès concurrentiel augmente le débit, mais il peut également créer des conflits de ressources partagées. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Concurrence](../../../../docs/framework/wcf/samples/concurrency.md).  
  
-   Limitation. Pour des performances optimales, limitez le nombre de messages dans le pipeline de répartiteur. Pour obtenir un exemple de procédure à suivre, consultez [limitation](../../../../docs/framework/wcf/samples/throttling.md).  
  
 Lorsque vous utilisez le traitement par lots, sachez que l'accès concurrentiel et la limitation se traduisent par des lots simultanés.  
  
 Pour obtenir un débit et une disponibilité supérieurs, utilisez une batterie de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui lisent les messages dans la file d'attente. Cela nécessite que tous ces services exposent le même contrat sur le même point de terminaison. Cette approche fonctionne le mieux pour les applications qui ont des taux élevés de production de messages parce qu'elle active plusieurs services qui lisent les messages dans la même file d'attente.  
  
 Lorsque vous utilisez des batteries de services, sachez que MSMQ 3.0 ne prend pas en charge les lectures transactionnelles à distance. MSMQ 4.0 prend en charge les lectures transactionnelles à distance.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Le traitement par lot des Messages dans une Transaction](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) et [les différences dans les files d’attente de fonctionnalités dans Windows Vista, Windows Server 2003 et Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>Mise en file d'attente avec sémantique d'unité de travail  
 Dans certains scénarios, les messages d'un groupe dans une file d'attente peuvent être liés et, par conséquent, l'ordre de ces messages est significatif. Dans de tels scénarios, traitez le groupe de messages connexes comme une unité unique : soit tous les messages sont traités avec succès, soit aucun ne l'est. Pour implémenter un tel comportement, utilisez des sessions avec files d'attente.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Regroupant les Messages en file d’attente dans une Session](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Corrélation des messages demande-réponse  
 Bien que les files d'attente soient en général unidirectionnelles, dans certains scénarios vous pouvez corréler une réponse reçue à une demande envoyée plus tôt. Si vous avez besoin d'une telle corrélation, il est recommandé d'insérer votre propre en-tête de message SOAP qui contient des informations de corrélation dans le message. En général, l'expéditeur joint cet en-tête avec le message, et le récepteur, en traitant le message et en y répondant avec un nouveau message sur une file d'attente de réponse, joint l'en-tête du message de l'expéditeur qui contient les informations de corrélation afin que l'expéditeur puisse identifier le message de réponse en relation avec le message de demande.  
  
## <a name="integrating-with-non-wcf-applications"></a>Intégration à des applications non WCF  
 Utilisez `MsmqIntegrationBinding` lors de l'intégration des services ou des clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à des services ou clients non [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. L'application non [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut être une application MSMQ écrite à l'aide de System.Messaging, COM+ [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou C++.  
  
 Lorsque vous utilisez `MsmqIntegrationBinding`, sachez ce qui suit :  
  
-   Un corps de message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'est pas identique à un corps de message MSMQ. Lors de l'envoi d'un message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide d'une liaison mise en file d'attente, le corps du message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est placé dans un message MSMQ. L'infrastructure MSMQ oublie cette information supplémentaire ; elle ne voit que le message MSMQ.  
  
-   `MsmqIntegrationBinding` prend en charge les types de sérialisation les plus courants. Selon le type de sérialisation, le type de corps du message générique, <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, prend des paramètres de type différents. Par exemple, <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> requiert `MsmqMessage\<byte[]>` et <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> requiert `MsmqMessage<Stream>`.  
  
-   Avec la sérialisation XML, vous pouvez spécifier le type connu à l’aide de la `KnownTypes` de l’attribut le [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) élément qui est ensuite utilisé pour déterminer comment désérialiser le message XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Queuing dans WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Comment : Exchange en file d’attente de Messages avec des points de terminaison WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Comment : échanger des Messages avec des points de terminaison WCF et les Applications Message Queuing](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Regroupement en attente de Messages dans une Session](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 [Le traitement par lot des Messages dans une Transaction](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 [À l’aide de files d’attente de lettres mortes pour gérer les échecs de transfert de Message](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [Gestion des messages incohérents](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Différences de fonctionnalités de file d’attente dans Windows Vista, Windows Server 2003 et Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [Sécurisation des Messages à l’aide de la sécurité de Transport](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [Sécurisation des Messages à l’aide de la sécurité des messages](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 [Résolution des problèmes de messagerie en file d’attente](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
