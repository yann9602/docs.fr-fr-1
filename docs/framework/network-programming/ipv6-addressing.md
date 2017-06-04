---
title: "Adressage IPv6 | Microsoft Docs"
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
  - "protocole Internet version 6, adresses dans"
  - "Découverte de voisin"
  - "IPv6, activer"
  - "IPv6, mobilité et"
  - "protocole Internet version 6, adresses anycast"
  - "IPv6, découverte de voisin"
  - "protocole Internet version 6, configurer automatiquement"
  - "protocole Internet version 6, activer"
  - "IPv6, adresses de monodiffusion"
  - "IPv6, configurer automatiquement"
  - "protocole Internet version 6, router"
  - "IPv6, documents RFC"
  - "IPv6, router"
  - "protocole Internet version 6, désactiver"
  - "protocole Internet version 6, adresses de monodiffusion"
  - "IPv6, adresses de multidiffusion"
  - "protocole Internet version 6, mobilité et"
  - "protocole Internet version 6, documents RFC"
  - "protocole Internet version 6, découverte de voisin"
  - "IPv6, adresses anycast"
  - "protocole Internet version 6, adresses de multidiffusion"
  - "IPv6, adresses dans"
  - "IPv6, désactiver"
ms.assetid: 20a104ae-1649-4649-a005-531a5cf74c93
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# Adressage IPv6
Dans le protocole \(IPv6 IPv6\), les adresses sont 128 bits de temps.  Une raison pour l'échec d'un si grand espace d'adressage est de subdiviser les adresses disponibles dans la hiérarchie des domaines de routage qui reflètent la topologie d'Internet.  Une autre raison consiste à mapper les adresses des cartes réseau \(ou des interfaces\) qui connectent des périphériques réseau.  IPv6 comporte une fonction inhérente pour résoudre les adresses à leur plus bas, qui est le niveau d'interface réseau, et présente également des fonctions de configuration automatique.  
  
## Représentation textuelle  
 Voici les trois classiques formes utilisées pour représenter des adresses de IPv6 en tant que chaînes de texte :  
  
-   **Colon\-hexadecimal form**.  c'est la forme par défaut n:n:n:n:n:n:n:n.  Chaque n représente la valeur hexadécimale d'une des huit éléments 16 bits de l'adresse.  Par exemple : `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.  
  
-   **Compressed form**.  En raison de la longueur d'adresse, il est courant d'avoir des adresses qui contient une longue chaîne des zéros.  Pour simplifier en écrivant les adresses, utilisez la forme compressée, dans laquelle une séquence contiguë unique de 0 blocs sont représentées par un symbole à double deux\-points \(::\).  Ce symbole ne peut apparaître qu'une seule fois dans une adresse.  Par exemple, l'adresse multicast `FFED:0:0:0:0:BA98:3210:4562` dans le formulaire est compressé `FFED::BA98:3210:4562`.  L'adresse unicast `3FFE:FFFF:0:0:8:800:20C4:0` dans le formulaire est compressé `3FFE:FFFF::8:800:20C4:0`.  L'adresse `0:0:0:0:0:0:0:1` de réalimentation dans le formulaire est compressé `::`1.  L'adresse non spécifiée `0:0:0:0:0:0:0:0` dans le formulaire est compressé `::`.  
  
-   **Mixed form**.  Ce formulaire combine des adresses d'IPv4 et de IPv6.  Dans ce cas, la structure d'adresse est n:n:n:n:n:n:d.d.d.d, où chaque n représente les valeurs hexadécimales des six éléments 16 bits de poids fort d'adresse de IPv6, et chaque d représente la valeur décimale d'une adresse IPv4.  
  
## Types d'adresse  
 Les principaux bits dans l'adresse définissent le type spécifique de IPv6 adresse.  Le champ de longueur variable contenant ces clés bits est appelé un préfixe \(FP\) de format.  
  
 Une adresse unicast de IPv6 est divisée en deux parties.  La première partie contient le préfixe d'adresse, et la deuxième partie contient l'identificateur d'interface.  Une méthode concise pour exprimer une adresse IPv6\/combinaison de préfixe est la suivante : ipv6\-address\/longueur de préfixe.  
  
 Voici un exemple d'une adresse avec un préfixe 64 bits.  
  
 `3FFE:FFFF:0:CD30:0:0:0:0/64`.  
  
 Le préfixe dans cet exemple est `3FFE:FFFF:0:CD30`.  L'adresse peut également être écrite dans un formulaire compressée, comme `3FFE:FFFF:0:CD30::/64`.  
  
 IPv6 définit les types suivants d'adresse :  
  
-   **Unicast address**.  Un identificateur pour une interface unique.  Un à en\-tête pack envoyé à cette adresse est envoyé à l'interface reconnue.  Les adresses unicasts se distinguent des adresses multicasts par la valeur de l'octet de poids fort.  l'octet de poids fort des adresses multicasts a la valeur hexadécimale du FF.  Toute autre valeur pour l'octet identifie une adresse unicast.  Voici les différents types d'adresses unicasts :  
  
    -   **Link\-local addresses**.  Les adresses sont utilisées sur un lien unique et ont le format suivant : FE80::*InterfaceID*.  Les adresses de lien local sont utilisées entre les nœuds sur un lien pour la configuration automatique d'adresse, découverte de voisins, ou lorsque aucun routeur n'est présent.  Une adresse de lien local est utilisée essentiellement au démarrage et lorsque le système n'a pas encore acquis des adresses d'une plus grande portée.  
  
    -   **Site\-local addresses**.  Les adresses sont utilisées sur un site unique et ont le format suivant : FEC0::*SubnetID*:*InterfaceID*.  Les adresses de site local sont utilisées pour répondre à l'intérieur d'un site sans nécessiter de préfixe global.  
  
    -   **Global IPv6 unicast addresses**.  Les adresses peuvent être utilisés à l'échelle Internet et avoir le format suivant : \(point gel, 3 bits\) l'ID de TLA 010 \(13 bits\) a réservé \(8 bits\) l'ID de SLA d'ID de NLA \(24 bits\) \(16 bits\) *InterfaceID* \(64 bits\).  
  
-   **Multicast address**.  Un identificateur pour un jeu d'interfaces appartenant \(en général à chaque nœud\).  Un à en\-tête pack envoyé à cette adresse est remis à toutes les interfaces identifiées par l'adresse.  Les types d'adresse multicast remplacent les adresses de distribution IPv4.  
  
-   **Anycast address**.  Un identificateur pour un jeu d'interfaces appartenant \(en général à chaque nœud\).  Un à en\-tête pack envoyé à cette adresse est remis à une seule interface identifiée par l'adresse.  Il s'agit de l'interface la plus proche identifiée comme lorsque le routage des métriques.  Les adresses anycasts sont prises de l'espace adresse d'adresse unicast et ne sont syntaxiquement pas perceptibles.  L'interface traité exécute la distinction entre la monodiffusion et les adresses anycasts en fonction de sa configuration.  
  
 En général un nœud a toujours une adresse de lien local.  Il peut avoir une adresse de site local et un ou plusieurs adresses globales.  
  
## Voir aussi  
 [Protocole Internet version 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)   
 [Sockets](../../../docs/framework/network-programming/sockets.md)