---
title: "protocole PNRP | Microsoft Docs"
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
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# protocole PNRP
Dans les environnements égal, les systèmes spécifiques de résolution de noms d'utilisation des homologues pour résoudre des emplacements réseau de et \(adresses, protocoles, et ports\) des noms ou d'autres types d'identificateurs.  Dans le passé, la résolution de noms homologue a été complexe par la connectivité fondamentalement transitoire ainsi que d'autres points faibles dans le DNS \(DNS\).  
  
 La plateforme de réseau égal Microsoft® Windows® résout le problème avec le protocole homologue \(PNRP\) de résolution du nom, un protocole sécurisé, évolutif, et dynamique d'inscription des noms et de résolution de noms d'abord développé pour Windows XP et ensuite mis à jour dans le ™ Windows Vista.  Fonctionnement de PNRP très différente des systèmes traditionnels de résolution de noms, ouvrant excitant de nouvelles possibilités pour les développeurs d'applications.  
  
 Avec PNRP, les noms équivalents peuvent être appliqués à l'ordinateur, ou des applications individuelles ou des services sur l'ordinateur.  Une résolution de noms homologue inclut une adresse, le port, et éventuellement une charge étendue.  Les avantages de ce système n'incluent la tolérance aux pannes, un goulot d'étranglement, et les résolutions du nom qui ne retournent jamais les adresses périmées ; faisant au protocole une excellente solution pour localiser les utilisateurs Mobiles.  
  
 En termes de sécurité, les noms équivalents peuvent être publiés comme sécurisé \(protected\) ou non protégée \(déprotégé\).  PNRP utilise le chiffrement à clé publique pour protéger des noms équivalents sécurisés à l'usurpation ; les ordinateurs et les services peuvent être nommés avec PNRP.  
  
-   Le protocole homologue de résolution de noms décrit les propriétés suivantes :  
  
-   Distribué et presque entièrement serverless.  Les serveurs sont uniquement requis pour le processus de départ.  
  
-   Définissez la composition de nom sans participation des tiers.  Contrairement à la composition de nom DNS, la composition de nom de PNRP est instantanée et sans coût œuvre.  
  
-   Mises à jour de PNRP en temps réel, ce qui empêché la résolution des adresses périmées.  
  
-   La résolution de noms via PNRP étend au delà des ordinateurs en autorisant également la résolution de noms pour les services.  
  
## L'espace de noms de System.Net.PeerToPeer  
  
-   La fonctionnalité de PNRP définie par l'espace de noms d' <xref:System.Net.PeerToPeer> dans le .NET Framework version 3.5.  Il fournit un ensemble de types qui peuvent être utilisés pour enregistrer et résoudre les noms équivalent à un service disponible de PNRP.  
  
-   \(PNRP et des programmes de résolution équivalents personnalisés peuvent être créés et instanciés à l'aide de les types fournis dans l'espace de noms d' <xref:System.ServiceModel.PeerResolvers> .\)  
  
-   Les types de base utilisés pour enregistrer et résoudre les noms avec un service disponible de PNRP sont les suivantes :  
  
-   <xref:System.Net.PeerToPeer.Cloud>: définit les informations décrivant un nuage disponible de PNRP, y compris sa portée.  
  
-   <xref:System.Net.PeerToPeer.PeerName>: Définit un nom homologue qui peut être utilisé pour stocker et résoudre ensuite un homologue dans un nuage.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord>: Définit l'enregistrement en nuage de PNRP qui contient les informations d'inscription pour un homologue, notamment les points de terminaison du réseau auquel l'homologue peut être contacté.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration>: Définit la procédure d'enregistrement pour un nom homologue, y compris des méthodes pour démarrer et arrêter l'inscription des noms homologue.  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver>: Définit le processus de résolution un nom homologue à ses points de terminaison du réseau, notamment synchrone et des méthodes asynchrones pour la résolution.  
  
## Voir aussi  
 <xref:System.ServiceModel.PeerResolvers>   
 <xref:System.Net.PeerToPeer>   
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)   
 [Exemple PeerToPeer de technologie](http://go.microsoft.com/fwlink/?LinkID=179571)