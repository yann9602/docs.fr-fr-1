---
title: "Extensibilit&#233; des canaux | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Extensibilit&#233; des canaux
Cette section contient des exemples qui illustrent des canaux personnalisés.  
  
## Dans cette section  
 [Local Channel](../../../../docs/framework/wcf/samples/local-channel.md)  
 Illustre le canal local, un canal du transport [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisé pour la communication dans un même domaine d'application.  
  
 [Reliable Secure Profile](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 Montre comment agencer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et Reliable Secure Profile \(RSP\).  
  
 [Custom Channel Dispatcher](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 Montre comment générer la pile de canaux de façon personnalisée en implémentant <xref:System.ServiceModel.ServiceHostBase> directement et comment créer un répartiteur de canal personnalisé dans un environnement avec hôte Web.  
  
 [Canal de segmentation](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 Montre comment limiter la mémoire utilisée pour mettre en mémoire tampon des messages volumineux envoyés à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [HTTP Acknowledgement Channel](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 Illustre un canal superposé qui modifie le modèle de messagerie unidirectionnel.  
  
 [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 Montre comment générer un canal de protocole personnalisé pour utiliser des cookies HTTP pour la gestion des sessions.  
  
 [Custom Message Interceptor](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 Montre comment implémenter un élément de liaison personnalisé qui crée des fabriques et des écouteurs de canaux pour intercepter tous les messages entrants et sortants à un point spécifique de la pile d'exécution.