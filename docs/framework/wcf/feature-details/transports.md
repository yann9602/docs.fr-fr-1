---
title: "Transports dans Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transports (WCF)"
  - "WCF, transports"
  - "Windows Communication Foundation, transports"
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# Transports dans Windows Communication Foundation
La couche de transport se situe tout en bas dans la pile des canaux.Les principaux transports utilisés dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont HTTP, HTTPS, TCP ainsi que les canaux nommés.Les rubriques de cette section contiennent des conseils et des instructions permettant de savoir quel protocole choisir, de le configurer et de définir les propriétés de réglage afférentes.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comporte des transports supplémentaires.Pour plus d'informations sur le transport de mise en file d'attente des messages \(Message Queuing, MSMQ\), consultez [Files d'attente et sessions fiables](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).Pour plus d'informations sur le transport pair à pair, consultez [Réseaux homologues](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## Dans cette section  
 [Choix d'un transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Présente les trois transports principaux et aborde les différents points à prendre en considération lors de leur sélection.  
  
 [Sélection d'un encodeur de message](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Aborde les facteurs à prendre en considération lors de la sélection d'un élément de liaison d'encodage de message.  
  
 [Transfert des messages par diffusion en continu](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Contient des instructions permettant de configurer la couche de transport pour une diffusion en continu.  
  
 [Configuration de HTTP et HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Contient des instructions permettant de configurer les éléments de liaison de transport HTTP et HTTPS.  
  
 [Procédure : remplacer la réservation d'URL WCF par une réservation restreinte](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Décrit comment utiliser les réservations restreintes de l'URL de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Quotas de transport](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Aborde les points à prendre en considération lors de la définition de quotas pour la couche de transport.  
  
 [Utilisation des NAT et des pare\-feu](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Contient des instructions permettant de configurer la couche de transport lorsque les messages envoyés ou reçus rencontrent un pare\-feu ou lorsqu'un traducteur d'adresses réseau \(NAT\) est utilisé.  
  
 [Partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Contient des instructions permettant d'utiliser le partage de port Net.TCP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Référence  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## Rubriques connexes  
 [Liaisons](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Extension de liaisons](../../../../docs/framework/wcf/extending/extending-bindings.md)