---
title: "Services fiables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrats de service (WCF), services fiables"
  - "WCF (WCF), messagerie fiable"
  - "WCF (WCF), sessions fiables"
  - "Windows Communication Foundation (WCF), messagerie fiable"
  - "Windows Communication Foundation (WCF), sessions fiables"
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Services fiables
Les files d'attente et les sessions fiables correspondent aux fonctionnalités [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] qui implémentent la messagerie fiable.Cette rubrique contient des explications sur les fonctionnalités de messagerie fiable de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 *La messagerie fiable* correspond à un dispositif selon lequel une source de messagerie fiable \(appelée la *source*\) transfère de manière fiable des messages vers une destination de messagerie fiable \(appelée la *destination*\).  
  
 La messagerie fiable effectue les tâches suivantes :  
  
-   Elle assure le transfert des assurances de messages envoyés depuis une source vers une destination, et ce quelles que soient les défaillances rencontrées par le transport ou le transfert de ces messages.  
  
-   Elle sépare la source de la destination.Ceci garantit l'indépendance des systèmes de défaillance et de récupération de la source et de la destination ainsi que le transfert et la remise fiables des messages même en cas d'indisponibilité de l'une ou de l'autre.  
  
 La messagerie fiable présente l'inconvénient d'engendrer une latence élevée.*La latence* correspond au temps nécessaire au message pour parvenir à la destination depuis la source.[!INCLUDE[indigo2](../../../includes/indigo2-md.md)], par conséquent, propose les types suivants de messageries fiables :  
  
-   [Sessions fiables](../../../docs/framework/wcf/feature-details/reliable-sessions.md) : offre un transfert fiable sans engendrer de latence élevée.  
  
-   [Files d'attente dans WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md) : permet à la fois les transferts fiables et la séparation entre source et destination.  
  
## Sessions fiables  
 À l'aide du protocole WS\-Reliable Messaging, les sessions fiables assurent un transfert fiable des messages de bout en bout entre source et destination quels que soient les nombre et type d'intermédiaires figurant entre les points de terminaison \(source et destination\) de la messagerie.Au rang de ces intermédiaires figurent notamment tous les transports qui n'utilisent pas le protocole SOAP \(par exemple, les proxys HTTP\) ou les intermédiaires qui utilisent SOAP \(par exemple, les routeurs ou les ponts SOAP\) et qui sont nécessaires à la circulation des messages entre les points de terminaison.Les sessions fiables utilisent une fenêtre de transfert en mémoire pour masquer les défaillances survenant au niveau des messages SOAP et rétablir les connexions en cas de défaillance des transports.  
  
 Les sessions fiables assurent le transfert fiable à faible latence des messages.Elles accomplissent pour les messages SOAP sur tous proxys ou intermédiaires, ce que le service TCP accomplit pour les paquets sur les ponts IP.[!INCLUDE[crabout](../../../includes/crabout-md.md)] les sessions fiables, consultez [Sessions fiables](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### Files d'attente  
 Les files d'attente dans [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] permettent à la fois le transfert fiable des messages et la séparation entre source et destination mais à haute latence.La communication en file d'attente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est créée par\-dessus Message Queuing \(MSMQ\).  
  
 Le service MSMQ est un composant en option de Windows.Ce service s'exécute en tant que service Windows.Il capture, au nom de la source, les messages à transmettre figurant dans la file d'attente de transmission, puis les remet à la file d'attente cible.La file d'attente cible accepte ces messages au nom de la destination pour les lui remettre ultérieurement dès qu'elle en fera la demande.Les gestionnaires MSMQ implémentent un protocole de transfert de message fiable afin d'éviter que les messages ne soient égarés pendant leur transmission.Il peut s'agir d'un protocole natif ou du protocole SOAP appelé protocole SRMP \(SOAP Reliable Messaging Protocole\).  
  
 La séparation, associée aux transferts fiables de messages entre les files d'attente, permet aux applications faiblement couplées de communiquer de manière fiable.À la différence des sessions fiables, dans le cadre d'une séparation, la source et la destination n'ont pas besoin de s'exécuter simultanément.Cela permet, de manière indirecte, d'utiliser les files d'attente comme dispositif de régulation de la charge lorsqu'il y a un écart entre le taux de production de messages de la source et le taux de réception de messages de la destination.[!INCLUDE[crabout](../../../includes/crabout-md.md)] les files d'attente, consultez [Files d'attente dans WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## Voir aussi  
 [Vue d'ensemble des sessions fiables](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
 [Mise en file d'attente dans WCF](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)