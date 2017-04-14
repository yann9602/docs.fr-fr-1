---
title: "&#192; propos de l’espace de noms System.Net.PeerToPeer.Collaboration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
caps.latest.revision: 4
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 4
---
# &#192; propos de l’espace de noms System.Net.PeerToPeer.Collaboration
L'espace de noms d' <xref:System.Net.PeerToPeer.Collaboration> fournit des classes et des interfaces utilisées pour implémenter des activités de collaboration pair de pair à l'aide de l'infrastructure égal de collaboration.  
  
## Classes  
 Les classes principales utilisées dans l'implémentation d'une activité égal de collaboration sont :  
  
-   <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, qui peut être utilisé pour stocker les contacts équivalents.  
  
-   <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> dans lequel à collaborer, comme un jeu, un client de conversation, ou une solution de conférence.  
  
-   Les homologues qui collaboreront à une activité.  Ces équivalents peuvent être représentés comme <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, ou objets d' <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> .  
  
-   La classe statique d' <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> elle\-même, qui spécifie les applications sont disponibles et les homologues participent à eux.  
  
 Les méthodes d' <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> sont utilisées pour demander des homologues à une session de collaboration.  Un homologue appelant peut s'abonner à un autre homologue pour les événements qui signalent les mises à jour de l'application, à l'objet, ou aux informations de présence affiliées à la session de collaboration.  Les classes de présence de spécifier si <xref:System.Net.PeerToPeer.Collaboration.Peer> est disponible pour la collaboration, et la classe d' <xref:System.Net.PeerToPeer.Collaboration.PeerScope> est utilisée pour spécifier le nombre de participation est autorisée pour un homologue : <xref:System.Net.PeerToPeer.Collaboration.PeerScope> \(global\), <xref:System.Net.PeerToPeer.Collaboration.PeerScope>, \(recommandé\) ou <xref:System.Net.PeerToPeer.Collaboration.PeerScope>.  
  
 Une session de collaboration est composée de quatre étapes :  
  
-   Découverte.  Découvrez ou publier des applications, les équivalents, et les informations de présence.  Par exemple, rechercher d'autres personnes sur le sous\-réseau local qui font installer les mêmes jeux.  
  
-   Appelant sur.  Envoyer et recevoir des invitations sécurisées pour les homologues commencent distants ou de joindre des sessions d' <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> .  
  
-   Gestion des contacts.  Add a découvert des homologues comme contact à <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.  
  
-   Communication.  Lorsque la communication est générée, utilisez les API d' <xref:System.Net> , l'API d' <xref:System.Net.PeerToPeer> , ou le canal pair de Windows Communication Foundation classe pour les communications multipartistes.  
  
 Par exemple, l'homologue hôte démarre une session de collaboration, puis utilise la méthode d' <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> pour ajouter un homologue distant et un de ses homologues locaux au gestionnaire de contacts du hébergent l'homologue.  Les trois utilisateurs participeront ensuite à leur propre session privée de collaboration.  
  
 Les applications P2P classiques sont : conférences téléphoniques pour REMARQUE\- prendre ou whiteboarding de collaboration, les applications serverless de conversation, annonces interactives, et sessions en ligne de jeu.  
  
## Voir aussi  
 <xref:System.Net.PeerToPeer.Collaboration>