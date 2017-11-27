---
title: Transports dans Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 115e2a69c7d990c7d4c59634644fb557e83ad405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="transports-in-windows-communication-foundation"></a>Transports dans Windows Communication Foundation
La couche de transport se situe au niveau le plus bas de la pile des canaux. Les principaux transports utilisés dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont HTTP, HTTPS, TCP ainsi que les canaux nommés. Les rubriques de cette section contiennent des conseils et des instructions permettant de savoir quel protocole choisir, de le configurer et de définir les propriétés de réglage afférentes.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comporte des transports supplémentaires. Pour plus d’informations sur le transport Message Queuing (également appelé MSMQ), consultez [les files d’attente et les Sessions fiables](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Pour plus d’informations sur le transport d’homologue à homologue, consultez [mise en réseau pair à pair](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Choix d’un Transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Présente les trois transports principaux et aborde les différents points à prendre en considération lors de leur sélection.  
  
 [Choix d’un encodeur de Message](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Aborde les facteurs à prendre en considération lors de la sélection d’un élément de liaison d’encodage de message.  
  
 [Transfert de messages en continu](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Contient des instructions permettant de configurer la couche de transport pour une diffusion en continu.  
  
 [Configuration de HTTP et HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Contient des instructions permettant de configurer les éléments de liaison de transport HTTP et HTTPS.  
  
 [Comment : remplacer la réservation d’URL WCF par une réservation restreinte](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Décrit comment utiliser les réservations restreintes de l'URL de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Quotas de transport](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Aborde les points à prendre en considération lors de la définition de quotas pour la couche de transport.  
  
 [Utilisation des NAT et pare-feu](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Contient des instructions permettant de configurer la couche de transport lorsque les messages envoyés ou reçus rencontrent un pare-feu ou lorsqu'un traducteur d'adresses réseau (NAT) est utilisé.  
  
 [Partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Contient des instructions permettant d'utiliser le partage de port Net.TCP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Liaisons](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Extension de liaisons](../../../../docs/framework/wcf/extending/extending-bindings.md)
