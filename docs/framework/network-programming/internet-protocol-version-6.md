---
title: "Protocole Internet version&#160;6 | Microsoft Docs"
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
helpviewer_keywords: 
  - "IPv6, améliorations"
  - "IPv4"
  - "IPv6"
  - "Protocole Internet version 6, améliorations"
  - "Protocole Internet version 6"
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# Protocole Internet version&#160;6
Le protocole \(IPv6 IPv6\) est une nouvelle suite de protocoles standard pour la couche réseau à partir de Internet.  IPv6 est conçu pour résoudre de nombreux problèmes de la version actuelle de la suite de les protocoles Internet \(appelées l'IPv4\) en ce qui concerne l'épuisement d'adresse, sécurité, configuration automatique, extensibilité, et ainsi de suite.  IPv6 développe les fonctions de Internet pour activer de nouveaux types d'applications, y compris les applications égal et mobiles.  Voici les problèmes majeurs du protocole IPv4 actuel :  
  
-   Épuisement rapide de l'espace d'adressage.  
  
     Cela est mené à l'utilisation des traducteurs \(NATs\) d'adresse réseau plusieurs adresses privées de cette carte à une adresse IP publique unique.  Les principaux problèmes créés par ce mécanisme gèrent la charge mémoire et le manque de connectivité de bout en bout.  
  
-   Échec de prise en charge de la hiérarchie.  
  
     En raison de son organisation prédéfinie inhérente de classe, l'IPv4 échec du véritable support hiérarchique.  Il est impossible de structurer les adresses IP d'une façon qui mappe réellement la topologie réseau.  Ce défaut de conception crucial crée le besoin de grandes tables de routage de la remise des paquets IPv4 à un emplacement quelconque sur Internet.  
  
-   Configuration réseau complexes.  
  
     Avec l'IPv4, les adresses doivent être assignées de manière statique ou à l'aide d'un protocole de configuration tel que le DHCP.  Dans une situation idéale, les hôtes ne doivent pas compter sur la gestion d'une infrastructure de DHCP.  À la place, ils peuvent se configurer sur le segment réseau dans lequel ils se trouvent.  
  
-   Manque d'authentification intégrée et de confidentialité.  
  
     L'IPv4 ne nécessite la prise en charge de aucun mécanisme qui fournit l'authentification ou le chiffrement des données échangées.  Cela modifie IPv6 avec.  La sécurité du protocole internet \(IPsec\) est une spécification de prise en charge de IPv6.  
  
 Un nouvel ensemble des protocoles doit satisfaire les spécifications de base suivantes :  
  
-   Routage et adressage à grande échelle avec la faible charge.  
  
-   Configuration automatique pour différentes situations connexion est.  
  
-   Authentification intégrée et de confidentialité.  
  
 Pour plus d'informations, consultez [Adressage IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [Routage IPv6](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6, configuration automatique](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Activation et désactivation d’IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md) et [Comment : modifier le fichier de configuration de l’ordinateur pour activer la prise en charge IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## Références  
 Voici les documents sélectionnés RFC que vous pouvez trouver au site de groupe de travail IETF \([http:\/\/www.ietf.org](http://www.ietf.org/)\) :  
  
-   La norme RFC 1287, vers la future architecture Internet.  
  
-   La norme RFC 1454, comparaison des propositions pour la version suivante de l'IP.  
  
-   La norme RFC 2373, architecture d'adressage de la version 6 d'adresses.  
  
-   La norme RFC 2374, un format global pouvant être regroupé en agrégats d'adresse d'unicast IPv6.  
  
 Vous pouvez également rechercher des informations d'IPv6\-related sur [Région de IPv6 sur Technet](http://go.microsoft.com/fwlink/?LinkID=179658).  
  
## Voir aussi  
 [Exemple de sockets de IPv6](http://go.microsoft.com/fwlink/?LinkID=179568)   
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)   
 [Sockets](../../../docs/framework/network-programming/sockets.md)