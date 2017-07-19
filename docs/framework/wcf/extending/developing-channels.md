---
title: "D&#233;veloppement de canaux | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# D&#233;veloppement de canaux
Le développement d'un protocole ou d'un canal de transport compatible avec la couche d'application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] s'effectue en plusieurs étapes.Cette rubrique liste ces étapes et renvoie à des rubriques spécifiques qui vous permettront d'en savoir plus.Pour comprendre le fonctionnement d'un modèle de canal et des divers types mentionnés dans cette rubrique, consultez [Vue d'ensemble du modèle de canal](../../../../docs/framework/wcf/extending/channel-model-overview.md).Pour un exemple exhaustif de canal du transport, consultez [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
## Liste des tâches à effectuer dans le cadre du développement d'un canal  
 Les étapes pour créer un canal défini par l'utilisateur sont les suivantes :Pour tous les canaux :  
  
1.  Choisissez quel modèle d'échange de messages de canal \(<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IReplyChannel>\) que vos <xref:System.ServiceModel.Channels.IChannelFactory> et <xref:System.ServiceModel.Channels.IChannelListener> prendront en charge. Décidez également si ces derniers devront prendre en charge les versions avec session de ces interfaces.Pour plus d'informations, consultez [Sélection d'un modèle d'échange de messages](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).  
  
2.  Créez une fabrication de canal ainsi qu'un écouteur \(<xref:System.ServiceModel.Channels.IChannelFactory> et <xref:System.ServiceModel.Channels.IChannelListener>\) qui prennent en charge votre modèle d'échange de messages.Pour plus d'informations sur le développement des fabrications, consultez [Client : fabrications de canaux et canaux](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md).Pour plus d'informations sur le développement des écouteurs, consultez [Service : écouteurs de canal et canaux](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).  
  
3.  Assurez\-vous que toutes les exceptions spécifiques au réseau sont normalisées en fonction de <xref:System.TimeoutException?displayProperty=fullName> ou de la classe dérivée appropriée de <xref:System.ServiceModel.CommunicationException>.Pour plus d'informations, consultez [Gestion des exceptions et des erreurs](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
4.  Pour permettre une utilisation depuis la couche d'application, ajoutez un <xref:System.ServiceModel.Channels.BindingElement> qui ajoute votre canal personnalisé à la pile des canaux.Pour plus d'informations, consultez [Création d'un élément de liaison](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).  
  
 Les étapes supplémentaires suivantes sont requises pour permettre une prise en charge plus exhaustive au niveau de la couche d'application :  
  
1.  Ajoutez une section d'extension d'élément de liaison afin d'exposer le nouvel élément de liaison au système de configuration.Pour plus d'informations, consultez [Prise en charge de la configuration et des métadonnées](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
2.  Ajoutez des extensions de métadonnées pour informer les autres points de terminaison des fonctionnalités disponibles.Pour plus d'informations, consultez [Prise en charge de la configuration et des métadonnées](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
3.  Ajoutez une liaison qui préconfigure une pile d'éléments de liaison d'après un profil précis.Pour plus d'informations, consultez [Création de liaisons définies par l'utilisateur](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
4.  Ajoutez une section de liaison ainsi qu'un élément de configuration de liaison afin d'exposer la liaison au système de configuration.Pour plus d'informations, consultez [Prise en charge de la configuration et des métadonnées](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
## Voir aussi  
 [Extension de liaisons](../../../../docs/framework/wcf/extending/extending-bindings.md)