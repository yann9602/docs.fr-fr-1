---
title: "Routage IPv6 | Microsoft Docs"
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
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
caps.latest.revision: 4
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 4
---
# Routage IPv6
Un mécanisme souple de routage est un avantage de IPv6.  En raison de la méthode pour laquelle les ID de réseau IPv4 étaient et sont alloués, de grandes tables de routage doivent être conservées par les routeurs qui sont sur Internet des circuits principaux.  Ces routeurs doivent connaître tous les itinéraires afin de transférer les packs qui sont potentiellement dirigés à n'importe quel nœud sur Internet.  Avec sa capacité à agréger des adresses, IPv6 permet d'adressage flexible et réduit radicalement la taille des tables de routage.  Dans cette nouvelle architecture d'adressage, les routeurs intermédiaires doivent protéger la trace uniquement de la partie locale de leur réseau afin de transférer des messages de manière appropriée.  
  
## Découverte de voisins  
 Certaines fonctionnalités fournies par la découverte de voisins sont :  
  
-   Découverte de routeur.  Cela permet aux hôtes d'identifier les routeurs locaux.  
  
-   Résolution d'adresse.  Cela permet aux nœuds pour résoudre une adresse de couche Liaison d'une adresse correspondante de saut prochain\- \(un remplacement pour ARP  \(\[ARP\]\).  
  
-   Configuration automatique d'adresse.  Cela permet aux hôtes pour configurer automatiquement le site local et des adresses globales.  
  
 La découverte de voisins utilise Internet Protocol gestionnaire de messages pour les messages d' IPv6 \(ICMPv6\) qui incluent :  
  
-   Publication de routeur.  Envoyé par un routeur sur une base pseudo\-périodique ou en réponse à une sollicitation de routeur.  Annonces de routeur d'utilisation de routeurs de IPv6 pour publier leur disponibilité, préfixes d'adresse, et d'autres paramètres.  
  
-   Sollicitation de routeur.  Envoyé par un hôte pour demander que les routeurs sur le lien envoient une annonce de routeur immédiatement.  
  
-   Sollicitation voisine.  Envoyé par des nœuds pour la résolution d'adresse, détection en double d'adresse, ou pour vérifier qu'un voisin est toujours accessible.  
  
-   Publication du voisin.  Envoyé par les nœuds pour répondre à la sollicitation voisine ou pour informer les voisins d'un changement de l'adresse de couche Liaison.  
  
-   Redirection.  Envoyé par les routeurs pour indiquer une meilleure adresse de saut prochain\- à une destination particulière pour un nœud d'émission.  
  
## Voir aussi  
 [Protocole Internet version 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)   
 [Sockets](../../../docs/framework/network-programming/sockets.md)