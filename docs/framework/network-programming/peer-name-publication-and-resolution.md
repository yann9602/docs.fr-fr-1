---
title: "R&#233;solution et publication de nom de pair | Microsoft Docs"
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
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# R&#233;solution et publication de nom de pair
## Publier un nom homologue  
 Pour publier un nouvel ID de PNRP, un homologue effectue les opérations suivantes :  
  
-   Envoie des messages de composition PNRP à ses voisins de cache \(les homologues qui ont stocké des ID de PNRP dans le plus bas du cache\) pour injecter les caches.  
  
-   Choisit les nœuds aléatoires dans le nuage qui ne sont pas ses voisins et les envoie des demandes de résolution de noms de PNRP pour sa propre identification P2P  Le processus résultant de détermination de point de terminaison injecte les caches des nœuds aléatoires dans le nuage avec l'ID de PNRP de l'homologue de publication.  
  
 Les nœuds de la version 2 de PNRP ne pas publier des ID de PNRP si elles résolvent que d'autres ID P2P.  Le HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\PeerNet\\PNRP\\IPV6\-Global\\SearchOnly\=1 registry value \(REG\_DWORD type\) specifies that peers only use PNRP pour la résolution de noms, jamais pour la composition de nom.  Cette valeur de Registre peut également être configurée par la stratégie de groupe.  
  
## Résoudre un nom homologue  
 Rechercher d'autres équivalents dans un réseau ou un nuage de PNRP est un processus consisté composé de deux phases :  
  
1.  Détermination de point de terminaison  
  
2.  Résolution d'ID de PNRP  
  
 Dans la phase de détermination de point de terminaison, un homologue qui tente de le résoudre l'ID de PNRP d'un service sur un autre ordinateur détermine l'adresse IPv6 de l'homologue distant.  L'homologue distant est celui qui a publié, ou est associé à, l'ID de PNRP de l'ordinateur ou service.  
  
 Après avoir confirmé que le point de terminaison distant a été enregistré en nuage de PNRP, l'homologue demandeur en phase de résolution d'ID de PNRP envoie une requête à ce point de terminaison homologue pour l'ID de PNRP du service souhaité.  Le point de terminaison envoie une réponse confirmant l'ID de PNRP du service, un commentaire, et de jusqu'à 4 kilo\-octets des informations supplémentaires que l'homologue demandeur peut utiliser pour la communication future.  Par exemple, si le point de terminaison souhaité est un serveur de jeu, les données équivalents supplémentaires d'enregistrement de noms peuvent contenir des informations sur le jeu, le niveau du jeu, et le nombre actuel de lecteurs.  
  
 Dans la phase de détermination de point de terminaison, PNRP utilise un processus itératif pour localiser le nœud qui a publié l'ID de PNRP, dans lequel le nœud effectuant la résolution est chargé de contacter les nœuds qui sont successivement plus proche de l'ID de PNRP cible  
  
 Pour effectuer la résolution de noms dans PNRP, l'homologue examine les entrées dans son propre cache d'une entrée correspondant à l'ID de PNRP cible  Si trouvé, l'homologue envoie un message de demande de PNRP à l'homologue et attend une réponse.  Si une entrée pour l'ID de PNRP est introuvable, l'homologue envoie un message de demande de PNRP à l'homologue qui correspond à l'entrée qui a un ID de PNRP qui correspond le mieux à l'identification de PNRP cible  Le nœud qui accepte le message de demande de PNRP examine son propre cache et effectue les opérations suivantes :  
  
-   Si l'ID de PNRP est trouvé, l'homologue demandé de point de terminaison répond directement à l'homologue demandeur.  
  
-   Si l'ID de PNRP est introuvable et un ID de PNRP dans le cache est plus proche de l'ID de PNRP cible, l'homologue demandé envoie une réponse à l'homologue demandeur qui contient l'adresse IPv6 de l'homologue qui représente l'entrée avec un ID de PNRP que correspond plus étroitement l'ID de PNRP cible  À l'aide de l'adresse IP en réponse, le nœud demandeur envoie un autre message de demande de PNRP à l'adresse IPv6 pour répondre ou pour examiner son cache.  
  
-   Si l'ID de PNRP est introuvable et il n'y a pas d'ID de PNRP dans son cache qui est plus proche de l'ID de PNRP cible, l'homologue demandé envoie l'homologue demandeur une réponse qui indique cette condition.  L'homologue demandeur choisit l'ID de PNRP prochain\- proche  
  
 L'homologue demandeur continue ce processus avec des itérations consécutives, localisation par la suite le nœud qui a signalé l'ID de PNRP  
  
 Dans l'espace de noms d' <xref:System.Net.PeerToPeer> , il existe une relation plusieurs à plusieurs entre les enregistrements d' <xref:System.Net.PeerToPeer.PeerName> qui contiennent les points de terminaison et les nuages ou des maillages de PNRP dans lesquels elles communiquent.  Lorsqu'il existe des entrées en double ou périmées, ou plusieurs nœuds ayant le même nom homologue, les nœuds de PNRP peuvent obtenir les informations actuelles à l'aide de la classe d' <xref:System.Net.PeerToPeer.PeerNameResolver> .  Les méthodes d' <xref:System.Net.PeerToPeer.PeerNameResolver> utilisent un homologue nom unique pour simplifier le point de vue d'enregistrements équivalent d'un à homologue\-à\- de nombreuses nom et au même un homologue à de nombreuses nuages.  Cela revient à une requête effectuée à l'aide d'une jointure de relationnel\- tableau.  Lors de l'achèvement réussi, l'objet du programme de résolution retourne <xref:System.Net.PeerToPeer.PeerNameRecordCollection> pour le nom homologue spécifié.  Par exemple, un nom homologue se produit dans tous les enregistrements équivalents de nom dans la collection, classée par le nuage.  Ce sont des instances du nom homologue dont les données de prise en charge peuvent être demandées par une application PNRP\- sur.  
  
## Voir aussi  
 <xref:System.Net.PeerToPeer>