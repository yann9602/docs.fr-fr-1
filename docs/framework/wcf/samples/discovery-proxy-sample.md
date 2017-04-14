---
title: "Exemple Discovery Proxy | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Exemple Discovery Proxy
Cet exemple montre comment créer une implémentation d'un proxy de découverte pour stocker des informations sur des services existants et comment des clients peuvent interroger ce proxy afin d'obtenir les informations.Cet exemple est composé de trois projets :  
  
-   **Service** : service de calculatrice [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] simple qui s'inscrit lui\-même auprès du proxy de découverte.  
  
-   **Discovery Proxy** : implémentation d'un service de proxy de découverte.  
  
-   **Client** : application cliente WCF qui appelle le proxy de découverte afin de rechercher des services.  
  
## Démonstrations  
 Implémentation du proxy de découverte  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## DiscoveryProxy  
 Dans la méthode `Main` du fichier Program.cs, l'exemple montre comment un service de type <xref:System.ServiceModel.Discovery.DiscoveryProxy> est hébergé.Il expose deux points de terminaison ; l'un de type <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>, l'autre de type <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>.Les points de terminaison utilisent tous deux un transport TCP.L'<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> écoute au niveau de l'URI spécifié par le paramètre `probeEndpointAddress`, là où les clients peuvent envoyer des messages Probe pour interroger le proxy afin d'obtenir ses données.Le <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> écoute au niveau de l'URI spécifié par le paramètre `announcementEndpointAddress`,là où le proxy écoute les annonces.Lorsqu'une annonce en ligne est reçue, le proxy ajoute le service à son cache et lorsqu'une annonce hors connexion est reçue, il supprime le service de son cache.  
  
 Le fichier DiscoveryProxy.cs contient l'implémentation du <xref:System.ServiceModel.Discovery.DiscoveryProxy>.Le proxy doit hériter de la classe <xref:System.ServiceModel.Discovery.DiscoveryProxyBase> et requiert une implémentation d'<xref:System.Runtime.Remoting.Messaging.AsyncResult>.À l'instanciation, le proxy crée un <xref:Systems.Collections.Generic.Dictionary%601>, qu'il utilise pour stocker les éléments qui lui sont connus.  
  
 Le fichier est divisé en deux régions, l'une pour les méthodes du cache du proxy, l'autre pour l'implémentation de Discovery Proxy.La région des méthodes du cache du proxy contient des méthodes utilisées pour mettre à jour le <xref:Systems.Collections.Generic.Dictionary%601>, exécuter des requêtes sur le <xref:Systems.Collections.Generic.Dictionary%601> et imprimer les données pour les utilisateurs.La région de l'implémentation de Discovery Proxy contient les méthodes substituées requises pour les fonctionnalités d'annonce et de sonde.Elles définissent les actions effectuées par un proxy après réception d'une annonce en ligne, d'une annonce hors connexion ou d'un message Probe.  
  
## Service  
 Dans le fichier Program.cs du projet Service, le même URI est utilisé pour le point de terminaison d'annonce et le proxy de découverte.En effet, le service utilise le point de terminaison pour l'envoi des annonces, alors que le proxy l'utilise pour leur réception.Le service utilise le <xref:System.ServiceModel.Discovery.DiscoveryBehavior> et lui ajoute un point de terminaison d'annonce.  
  
## Client  
 Le projet Client utilise le même URI pour son point de terminaison de sonde et le proxy.En effet, les sondes de ce scénario font également l'objet d'une monodiffusion spécifiquement vers le point de terminaison disponible sur le proxy.Le client se connecte à cette adresse bien connue, puis l'interroge au sujet du service.Une fois qu'il a trouvé le service, il s'y connecte.  
  
#### Pour utiliser cet exemple  
  
1.  Chargez la solution du projet dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] et générez le projet.  
  
2.  En premier lieu, exécutez l'application Discovery Proxy, générée dans \[répertoire de base de la solution\]\\DiscoveryProxy\\bin\\debug.Discovery Proxy doit s'exécuter en premier, car les points de terminaison d'annonce TCP doivent être en place pour permettre au service d'envoyer ses annonces.  
  
3.  En second lieu, exécutez l'application Service, générée dans \[répertoire de base de la solution\]\\Service\\bin\\debug.Au démarrage, le service envoie une annonce au point de terminaison d'annonce du proxy de découverte et est inscrit dans le cache du proxy.  
  
4.  Ensuite, exécutez l'application Client, générée dans \[répertoire de base de la solution\]\\Client\\bin\\debug.Le client interroge le proxy, obtient l'adresse du service, puis s'y connecte.  
  
5.  Enfin, arrêtez le client, le service, puis le proxy.Pour recevoir l'annonce hors connexion du service, le proxy doit être en cours d'exécution.  
  
## Voir aussi