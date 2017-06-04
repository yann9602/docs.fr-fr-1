---
title: "Discovery Router Service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Discovery Router Service
Cet exemple montre comment transférer des messages de découverte à un autre point de terminaison.  
  
## Démonstrations  
 Routage de découverte  
  
## Discussion  
 Le routage de découverte est utile dans un scénario où un client recherche un service à l'aide d'un proxy et que le proxy ne connaît pas ce service, mais connaît l'existence d'un autre proxy.Ce proxy peut transférer le paquet de découverte de ce client au deuxième proxy.Le deuxième proxy peut rechercher le service et retourner les réponses au client d'origine.  
  
 Dans cet exemple, un client envoie un message à un composant de routage de découverte.Ce message est envoyé à un point de terminaison spécifique situé sur le routeur de découverte.Le routeur transfère alors le message à un point de terminaison de multidiffusion UDP.Le message Probe rejoint le point de terminaison de multidiffusion et un service à l'écoute d'une adresse de multidiffusion UDP répond à ce routeur de découverte.Le routeur de découverte collecte les réponses et les renvoie au client.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Générez l'exemple.  
  
2.  Exécutez le fichier exécutable DiscoveryRouter.  
  
3.  Exécutez le fichier exécutable du service à partir du répertoire de build.  
  
4.  Exécutez le fichier exécutable du client.Notez que le client trouve le service.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`