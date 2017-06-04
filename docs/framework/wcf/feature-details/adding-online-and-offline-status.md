---
title: "Ajout d&#39;&#233;tats en ligne et hors connexion | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Ajout d&#39;&#233;tats en ligne et hors connexion
Dans de nombreux cas, il est important qu'une application surveille les informations relatives à l'état d'une connexion de canal homologue.Vous pouvez obtenir ces informations en appelant la méthode `GetProperty` depuis une implémentation de l'interface <xref:System.ServiceModel.IOnlineStatus>.Un objet implémenté sur cette interface peut en effet surveiller l'état de la connexion ou s'inscrire à des gestionnaires d'événements, tels que `OnOnline` et `OnOffline`. Cet objet réagira immédiatement à toutes modifications de l'état en ligne.  
  
 Dans l'infrastructure de canal homologue, un client est considéré comme étant en ligne s'il est connecté à au moins un autre homologue et comme étant hors connexion dans le cas contraire.Ceci peut s'avérer particulièrement utile à la fois pour déboguer les applications en cours de développement ou pour communiquer des informations détaillées à l'utilisateur final.  
  
> [!NOTE]
>  Un gestionnaire d'événements en ligne doit en premier lieu garantir l'ouverture du nœud avant l'envoi de tout message.  
  
## Voir aussi  
 [Création d'une application de canal homologue](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)