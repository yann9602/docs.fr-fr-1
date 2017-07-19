---
title: "Noms d’homologues et ID PNRP | Microsoft Docs"
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
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# Noms d’homologues et ID PNRP
Un nom homologue représente un point de terminaison de communication, qui peut être un ordinateur, un utilisateur, un groupe, un service, ou un élément associé à un homologue qui peut être résolu à une adresse IPv6.  Le protocole homologue \(PNRP\) de résolution de noms prend le nom homologue statistiquement uniques pour la création d'un ID de PNRP, qui est utilisé pour identifier des membres nuage.  
  
## Noms homologues  
 Les noms équivalents peuvent être stockés comme non protégée ou être sécurisés.  Les noms non protégée sont simplement des chaînes de texte auxquelles sont soumises à l'usurpation, comme n'importe qui peut enregistrer un nom non protégée en double.  Les noms non protégée mieux sont utilisés dans les réseaux privés ou sinon protégés.  Les noms sécurisés sont protégés avec un certificat et une signature numérique.  Uniquement l'éditeur d'origine pourra afficher la propriété d'un nom sécurisé.  
  
 La combinaison de nuage et la portée raisonnablement fournit un environnement sécurisé pour les homologues qui participent à l'activité de PNRP.  Toutefois, l'utilisation d'un nom homologue sécurisé ne garantit pas la sécurité globale de l'application de mise en réseau.  La sécurité de l'application est dépendante de l'implémentation.  
  
 Les noms équivalents sécurisés sont stockés uniquement par leur propriétaire et sont protégés avec le chiffrement à clé publique.  Un nom homologue sécurisé est considéré comme appartenant à l'entité homologue ayant la clé privée correspondante.  La propriété peut être prouvée via l'adresse homologue certifiée \(CPA\), qui est signé à l'aide de la clé privée.  Un utilisateur malveillant ne peut pas modifier la propriété d'un nom homologue sans clé privée correspondante.  
  
## ID de PNRP  
 ![ID PNRP](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.png "fdc9e8a0\-4a1c\-488d\-a019\-bc3a1973220c")  
  
 Les ID de PNRP sont composés des éléments suivants :  
  
-   Les 128 bits de poids fort, appelée l'ID \(P2P égal\), sont hachage d'un homologue nom assigné au point de terminaison.  Le nom homologue a le format suivant : *Authority.Classifier*.  Pour les noms sécurisés, *l'autorité* est le hachage de l'algorithme de hachage sécurisé 1 \(SHA1\) de la clé publique du nom homologue caractères hexadécimaux.  Pour les noms non protégée, *l'autorité* est le seul caractère « 0 ".  *Le classifieur* est une chaîne qui identifie l'application.  Un classifieur homologue de nom ne peut être supérieur à 149 caractères, y compris le Terminator d' `null` .  
  
-   Les 128 bits de poids faible sont utilisés pour l'emplacement de service, qui est un nombre généré qui identifie plusieurs instances du même ID P2P dans le même nuage.  
  
 Cette combinaison d'emplacement et d'ID de service P2P permet de plusieurs identificateurs de PNRP à stocker d'un ordinateur unique.  
  
## Voir aussi  
 <xref:System.Net.PeerToPeer.PeerName>   
 <xref:System.Net.PeerToPeer>