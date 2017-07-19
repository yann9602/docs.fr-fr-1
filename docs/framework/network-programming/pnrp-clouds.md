---
title: "Nuages PNRP | Microsoft Docs"
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
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: 4
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 4
---
# Nuages PNRP
PNRP « nuage » représente un ensemble de nœuds qui peuvent communiquer sur le réseau.  Le terme « nuage » est un synonyme de « maillage homologue » et « égal » graphique.  
  
 La communication entre nœuds ne doit jamais traverser d'un nuage à un autre.  Une instance <xref:System.Net.PeerToPeer.Cloud> est identifiée de manière unique par son nom, qui respecte la casse.  Un nœud ou un homologue unique peut être connecté à plusieurs nuages.  
  
 Les nuages sont très liés aux interfaces réseau.  Sur un ordinateur multirésident avec deux cartes réseau connectées à différents sous\-réseaux, trois nuages seront retournés : un pour chacune des adresses de lien local par interface et un nuage de portée globale unique.  
  
 Le utilise trois de PNRP opacifient les portées «  », dans lesquelles une portée est un regroupement des ordinateurs qui peuvent se trouver :  
  
-   Le nuage global correspond à la portée globale d'adresse IPv6 et les adresses globales et représente tous les ordinateurs sur Internet IPv6 entier.  Il y a un seul nuage global unique.  
  
-   Le nuage de lien local correspond à la portée et des adresses de lien local de lien local de IPv6 adresse.  Un nuage de lien local est pour un lien spécifique, qui est généralement le même que le sous\-réseau local attaché.  Il peut y avoir des nuages de lien local multiples.  
  
 Un troisième nuage, le nuage spécifique au site, correspond à la portée et des adresses de site local de IPv6 adresse de site.  Ce nuage a été déconseillé, bien qu'il soit toujours pris en charge dans PNRP.  
  
## Nuages  
 Les nuages de PNRP sont représentés par les instances de la classe d' <xref:System.Net.PeerToPeer.Cloud> .  Les groupes de nuages utilisaient un homologue sont représentés par les instances de la classe énumérable d' <xref:System.Net.PeerToPeer.CloudCollection> .  Les collections de nuages de PNRP connus à l'homologue actuel peuvent être obtenues en appelant la méthode statique d' <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> .  
  
 Les différents nuages ont des noms uniques, représentés comme une chaîne de 256 caractères Unicode.  Ces noms, avec la portée indiquée ci\-dessus, sont utilisés pour construire des seules instances avec de la classe nuage.  Ces instances peuvent être sérialisées et reconstruites pour l'utilisation persistant.  
  
 Une fois une instance nuage est créée ou des noms obtenus et homologues peuvent être enregistrés avec l'pour créer un maillage des homologues.  
  
## Voir aussi  
 <xref:System.Net.PeerToPeer.Cloud>   
 [protocole PNRP](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)