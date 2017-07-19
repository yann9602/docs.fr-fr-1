---
title: "Collaboration pair &#224; pair | Microsoft Docs"
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
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# Collaboration pair &#224; pair
Le réseau égal est l'utilisation d'ordinateurs relativement puissants \(ordinateurs personnels\) qui existent au bord de Internet pour plus que les tâches de calcul clientes.  \(PC\) De l'ordinateur personnel moderne est très un processeur rapide, une vaste mémoire, et un grand disque dur, aucun qui sont entièrement utilisés en exécutant des tâches de calcul courantes telles que la messagerie électronique et la navigation web.  PC moderne peut facilement jouer le rôle de client et serveur \(un homologue\) pour de nombreux types d'applications.  
  
-   L'infrastructure égal de collaboration est une implémentation simplifiée de l'infrastructure égal de Microsoft Windows qui tire parti du service du Voisinage immédiat dans Windows Vista et les plateformes ultérieures.  Elle est mieux utilisée pour les applications homologue\- activées dans un recommandé pour lequel le service du Voisinage immédiat s'exécute, bien qu'il puisse traiter les points de terminaison ou des contacts internet.  Elle incorpore le gestionnaire de contacts commun utilisé par Live Messenger et d'autres applications prenant Live\- de déterminer les points de terminaison, la disponibilité, et la présence de contact.  
  
## Applications de collaboration  
 Une application classique égal de collaboration est composée des étapes suivantes :  
  
-   L'homologue détermine l'identité d'un homologue qui s'intéresse héberger dans une session de collaboration  
  
-   Une demande d'héberger une session est envoyée, d'une certaine manière, et l'homologue hôte accepte de gérer l'activité de collaboration.  
  
-   L'hôte invite des contacts dans le sous\-réseau \(demandeur\) à une session.  
  
-   Tous les homologues qui souhaitent collaborer peuvent ajouter l'hôte à leurs gestionnaires de contacts.  
  
-   La plupart des homologues enverront des réponses en appelant sur, si accepté ou décliné, au hébergez l'homologue en temps voulu.  
  
-   Tous les homologues qui souhaitent collaborer les abonneront au hébergent l'homologue.  
  
-   Alors que les homologues effectuent leur activité initiale de collaboration, hébergez l'homologue peut ajouter les homologues distants à son gestionnaire de contacts.  Il gère également toutes les réponses en appelant sur pour déterminer qui a reçu, qui a refusé, et qui n'a pas répondu.  Elle peut annuler des invitations à ceux qui n'ont pas répondu, ou effectuer une autre activité.  
  
-   À ce stade, l'homologue hôte peut démarrer une session de collaboration avec tous les homologues invités, ou enregistrez une application avec l'infrastructure de collaboration.  Les applications utilisent l'infrastructure P2P égal de collaboration et l'espace de noms d' <xref:System.Net.PeerToPeer.Collaboration> pour coordonner les communications pour les jeux, les forums électroniques, la conférence, et d'autres applications serverless présence de.  
  
## Sécurité de réseau égal  
 Dans un domaine Active Directory, les contrôleurs de domaine fournissent des services d'authentification Kerberos à l'aide de.  Dans un environnement homologue serverless, les homologues doivent fournir leur propre authentification.  Pour le réseau égal, tout nœud peut agir comme une autorité de certification, supprimez la spécification d'un certificat racine dans la mémoire de la racine approuvée de chaque homologue.  L'authentification est fournie avec des certificats auto\-signés, mis en forme comme certificats X.509.  Ce sont des certificats créés par chaque homologue, qui génère des paires de clés publique\/clé privée et le certificat signé à l'aide de la clé privée.  Le certificat auto\-signé est utilisé pour l'authentification et pour fournir des informations sur l'entité homologue.  Comme l'authentification X.509, l'authentification homologue de mise en réseau compte lors d'une chaîne des certificats suivant à une clé publique qui est approuvée.  
  
## Voir aussi  
 <xref:System.Net.PeerToPeer.Collaboration>   
 [À propos de l’espace de noms System.Net.PeerToPeer.Collaboration](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)