---
title: "IPv6, configuration automatique | Microsoft Docs"
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
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# IPv6, configuration automatique
Un rôle important de IPv6 est de prendre en charge la technologie Plug AND Play de nœud.  Autrement dit, il doit être possible de passer un nœud à un réseau IPv6 et de le faire configurer automatiquement sans aucune interaction humaine.  
  
## Type de configuration automatique  
 IPv6 prend en charge les types suivants de configuration automatique :  
  
-   **Stateful auto\-configuration**.  Ce type de configuration requiert un certain niveau de l'interaction humaine car il a besoin d'un protocole DHCP du serveur de  IPv6 \(DHCPv6\) pour l'installation et la gestion des nœuds.  Le serveur DHCPv6 conserve une liste de nœuds auxquels il fournit des informations de configuration.  Il met également à jour les informations d'état ainsi le serveur sait le temps chaque adresse est en cours de utilisation, et lorsqu'elle peut être disponible pour la réassignation.  
  
-   **Stateless auto\-configuration**.  Ce type de configuration est appropriée pour les petites entreprise et des personnes.  Dans ce cas, chaque hôte détermine les adresses à partir de le contenu des annonces de routeur reçues.  À l'aide de la norme IEEE EUI\-64 pour définir la partie d'ID de réseau de l'adresse, il est judicieux d'en supposant que l'unicité de l'adresse de l'hôte sur le lien.  
  
 Indépendamment de la façon dont l'adresse est déterminée, le nœud doit vérifier que son adresse potentielle est unique au lien local.  Cela est fait en envoyant un message voisin de sollicitation à l'adresse potentielle.  Si le nœud reçoit une réponse, il sait que l'adresse est déjà utilisé et doit déterminer une autre adresse.  
  
## Mobilité de IPv6  
 La prolifération des appareils mobiles a introduit une nouvelle spécification : Un périphérique doit pouvoir modifier arbitrairement des emplacements sur Internet IPv6 et mettre à jour toujours les connexions existantes.  Pour fournir cette fonctionnalité, un nœud mobile est assigné une adresse personnelle à laquelle il peut toujours être atteint.  Lorsque le nœud est mobile d'accueil, il se connecte au lien d'accueil et utilise son adresse personnelle.  Lorsque le nœud mobile n'est pas domestique, un agent d'accueil, qui est généralement un routeur, des messages de entre suivre le nœud mobile et des nœuds avec lesquels il communique.  
  
## Voir aussi  
 [Protocole Internet version 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)   
 [Sockets](../../../docs/framework/network-programming/sockets.md)