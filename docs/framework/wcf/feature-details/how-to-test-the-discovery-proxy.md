---
title: "Proc&#233;dure&#160;: tester le proxy de d&#233;couverte | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Proc&#233;dure&#160;: tester le proxy de d&#233;couverte
Cette rubrique est la quatrième d'une série quatre qui expliquent comment implémenter un proxy de découverte.  Dans la rubrique précédente, [Procédure : implémenter une application cliente qui utilise le proxy de découverte pour rechercher un service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), vous avez implémenté une application cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que le proxy de découverte utilise pour rechercher un service avant de l'appeler.  Cette rubrique explique comment vérifier si le proxy de découverte, le service et l'application cliente fonctionnent comme prévu.  
  
### Exécuter le proxy de découverte  
  
1.  Ouvrez une invite de commandes en tant qu'administrateur.  
  
2.  Une boîte de dialogue s'affiche éventuellement, indiquant : le Pare\-feu Windows a bloqué certaines fonctionnalités de ce programme.  Si vous voyez ce message, cliquez sur le bouton **Débloquer**.  
  
3.  Dans l'invite de commandes, exécutez le proxy de découverte, DiscoveryProxy.exe.  
  
4.  L'application doit afficher le texte suivant : `Proxy started. Hit Enter to exit`.  
  
### Exécuter le service détectable  
  
1.  Ouvrez une invite de commandes en tant qu'administrateur.  
  
2.  Dans l'invite de commandes, exécutez le service détectable service.exe.  
  
3.  Le DiscoveryProxy.exe doit afficher le texte suivant : `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### Exécuter l'application cliente  
  
1.  Ouvrez une invite de commandes.  
  
2.  Dans l'invite de commandes, exécutez l'application client.exe.  
  
3.  Au bout de quelques secondes l'application cliente affiche le texte suivant : connexion au \[point de terminaison de service\].  
  
4.  Le service.exe doit ensuite afficher le texte suivant : message de salutation reçu, je vais répondre.  
  
5.  Le client.exe doit ensuite afficher le texte suivant : Bonjour client \!  
  
### Arrêter les applications  
  
1.  Arrêtez l'application cliente.  
  
2.  Arrêtez le service.  Le proxy de découverte affiche le texte suivant : `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.  
  
3.  Arrêtez le proxy de découverte.  
  
## Voir aussi  
 [Vue d'ensemble de la découverte WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)   
 [Procédure : implémenter un proxy de découverte](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)   
 [Procédure : implémenter un service détectable qui s'enregistre avec le proxy de découverte.](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)   
 [Procédure : implémenter une application cliente qui utilise le proxy de découverte pour rechercher un service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)