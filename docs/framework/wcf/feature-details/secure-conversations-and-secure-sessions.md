---
title: "Conversations s&#233;curis&#233;es et sessions s&#233;curis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# Conversations s&#233;curis&#233;es et sessions s&#233;curis&#233;es
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a la capacité d'établir des sessions sécurisées entre deux points de terminaison qui s'authentifient l'un l'autre et conviennent d'un chiffrement et d'un processus de signature numérique.Par exemple, le point de terminaison de service peut demander qu'un point de terminaison de client envoie un jeton de sécurité basé sur un certificat X.509 pour l'authentification.Une fois que le client est authentifié, le point de terminaison de service renvoie un jeton de contexte de sécurité \(SCT\) au client, utilisé ensuite pour sécuriser tous les messages suivants dans la session.L'établissement de cette session sécurisée permet d'améliorer l'ensemble des messages échangés entre les deux points de terminaison, parce que le SCT a une clé symétrique.Les clés asymétriques, sur lesquelles les certificats X.509 sont basés, requièrent beaucoup plus de puissance de calcul que les clés symétriques pour générer une signature numérique ou chiffrer un jeu de données.  
  
 La stratégie de démarrage \(définie dans la section 6.2.7 de la norme [WS\-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) \(page pouvant être en anglais\)\) contient les assertions de sécurité de message utilisées pour sécuriser le canal et authentifier le client avant l'échange RST\/SCT et RSTR\/SCT.Certaines liaisons standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ont une propriété `Security.Message.EstablishSecurityContext` qui contrôle si la conversation sécurisée est utilisée.Lorsque vous utilisez les liaisons personnalisées, le démarrage est indiqué en imbriquant les éléments de liaison de sécurité, soit par le biais de [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) dans le fichier de configuration, soit en appelant <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> dans le code.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les sessions, consultez [Utilisation de sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
## Voir aussi  
 [Sessions, instanciation et accès concurrentiel](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)   
 [Comment : créer un service qui requiert des sessions](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)