---
title: "Suivis principaux | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Suivis principaux
Cette rubrique répertorie quelques\-uns des suivis principaux émis par [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## Suivis principaux  
  
|Suivi|Description|  
|-----------|-----------------|  
|Suivi du journal des messages|Le suivi est émis lorsqu'un message [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] est enregistré par la fonctionnalité de journalisation des messages lorsque la source du suivi `System.ServiceModel.MessageLogging` est activée.Un clic sur ce suivi permet d'afficher le message.Il existe quatre points d'enregistrement configurables pour un message : `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, également indiqués par l'attribut Message Source dans le suivi du journal des messages.|  
|Suivi de message reçu|Ce suivi est émis lorsqu'un message [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] est reçu si la source du suivi `System.ServiceModel` est activée au niveau des informations ou des commentaires.Ce suivi est nécessaire pour consulter la flèche de la corrélation du message dans la vue du graphique d'activité.|  
|Suivi de message envoyé|Ce suivi est émis lorsqu'un message [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] est envoyé si la source du suivi `System.ServiceModel` est activée au niveau des informations ou des commentaires.Ce suivi est nécessaire pour consulter la flèche de la corrélation du message dans la vue du graphique d'activité.|  
|Obtenir ChannelEndpointElement|Ce suivi est émis dans la fabrication de canal Construct, au niveau des informations.Il fournit une description du point de terminaison auquel le client parle \(adresse distante, liaison, nom de contrat\).|  
|Obtenir ServiceElement|Ce suivi est émis dans l'hôte du service Construct, au niveau des informations.Il fournit une description du contrat de service et de la liaison.|  
|Créer SocketConnection|Ce suivi est émis dans la première action Process exécutée par le client et dans l'activité Receive bytes du service.Il fournit les adresses IP locale et distante.Il est émis au niveau Informations.|