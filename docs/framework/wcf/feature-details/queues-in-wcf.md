---
title: Files d'attente dans Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 279f6094b7e41549a285ac0175c3f949f9d8e7e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="queues-in-windows-communication-foundation"></a>Files d'attente dans Windows Communication Foundation
Les rubriques de cette section traitent de la prise en charge des files d'attente par [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge la mise en file d'attente en utilisant Microsoft Message Queuing (anciennement connu sous le nom MSMQ) comme un transport et active les scénarios suivants :  
  
-   Applications faiblement couplées. Les applications émettrices peuvent envoyer des messages aux files d'attente sans avoir besoin de savoir si l'application réceptrice est disponible pour traiter le message. La file d'attente permet l'indépendance du traitement, ce qui signifie que l'application émettrice peut envoyer des messages à la file d'attente à un taux de qui ne dépend pas de la rapidité avec laquelle les applications réceptrices peuvent traiter les messages. La disponibilité globale du système augmente lorsque l'envoi de messages à une file d'attente n'est pas fortement couplé au traitement du message.  
  
-   Isolation de défaillance. Les applications qui envoient des messages à une file d'attente ou en reçoivent peuvent échouer sans impact mutuel. Par exemple, si l'application réceptrice échoue, l'application émettrice peut continuer à envoyer des messages à la file d'attente. Lorsque le récepteur est de nouveau en service, il peut traiter les messages de la file d'attente. L'isolation de défaillance augmente la fiabilité globale du système et sa disponibilité.  
  
-   Nivellement de charge. Les applications émettrices peuvent submerger de messages les applications réceptrices. Les files d'attente peuvent gérer la production de messages et les taux consommation incompatibles afin qu'un récepteur ne soit pas submergé.  
  
-   Opérations hors circuit. L'envoi, la réception et le traitement d'opérations peut se faire hors circuit en cas de communication sur des réseaux à forte latence ou à disponibilité limitée, comme dans le cas des appareils mobiles. Les files d'attente permettent à ces opérations de se poursuivre, même lorsque les points de terminaison sont déconnectés. Lorsque la connexion est rétablie, la file d'attente envoie des messages à l'application réceptrice.  
  
 Pour utiliser la fonctionnalité de file d'attente dans une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous pouvez utiliser l'une des liaisons standard, ou vous pouvez créer une liaison personnalisée si aucune des liaisons standard ne correspond à vos spécifications. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les liaisons standard appropriés et comment choisir un, consultez [Comment : échanger des Messages avec les points de terminaison WCF et les Applications Message Queuing](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Création de liaisons personnalisées, consultez [des liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble des files d’attente](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Vue d'ensemble des concepts de la mise en file d'attente des messages.  
  
 [Queuing dans WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Vue d'ensemble de la prise en charge des files d'attente par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Comment : Exchange en file d’attente de Messages avec des points de terminaison WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Explique comment utiliser la classe <xref:System.ServiceModel.NetMsmqBinding> pour communiquer entre un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Comment : échanger des Messages avec des points de terminaison WCF et les Applications Message Queuing](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Explique comment utiliser la <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pour communiquer entre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et des applications Message Queuing.  
  
 [Regroupement en attente de Messages dans une Session](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Explique comment grouper des messages dans une file d'attente pour faciliter le traitement des messages corrélés par une application réceptrice unique.  
  
 [Le traitement par lot des Messages dans une Transaction](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Explique comment traiter par lots les messages dans une transaction.  
  
 [À l’aide de files d’attente de lettres mortes pour gérer les échecs de transfert de Message](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Explique comment gérer les échecs de transfert des messages et de livraison à l'aide des files d'attente de lettres mortes et comment traiter des messages de la file d'attente de lettres mortes.  
  
 [Gestion des messages incohérents](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Explique comment gérer les messages incohérents (messages qui ont dépassé le nombre maximal de tentatives de livraison à l'application réceptrice).  
  
 [Différences de fonctionnalités de file d’attente dans Windows Vista, Windows Server 2003 et Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Résume les différences des files d'attente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] et [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Sécurisation des Messages à l’aide de la sécurité de Transport](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Décrit comment utiliser la sécurité de transport pour sécuriser des messages mis en file d'attente.  
  
 [Sécurisation des Messages à l’aide de la sécurité des messages](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Décrit comment utiliser la sécurité des messages pour sécuriser des messages mis en file d'attente.  
  
 [Résolution des problèmes de messagerie en file d’attente](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Explique comment résoudre les problèmes courants de mise en file d'attente.  
  
 [Meilleures pratiques pour la Communication en file d’attente](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Explique les meilleures pratiques pour utiliser les communications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mises en file d'attente.  
  
## <a name="see-also"></a>Voir aussi  
 [Message Queuing](http://msdn.microsoft.com/en-us/ff917e87-05d5-478f-9430-0f560675ece1)
