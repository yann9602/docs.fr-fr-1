---
title: "Autorisations web et socket | Microsoft Docs"
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
  - "Réseau"
  - "positions (.NET Framework), accepter"
  - "sockets, autorisations"
  - "réseau, autorisations"
  - "Internet, autorisations"
  - "Ressources réseau"
  - "classe SocketPermission, à propos de la classe SocketPermission"
  - "positions (.NET Framework), connexion"
  - "classe WebPermission, à propos de la classe WebPermission"
  - "autorisations (.NET Framework), sockets"
  - "sécurité (.NET Framework), Internet"
  - "positions (.NET Framework), octroyer"
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Autorisations web et socket
La sécurité internet pour les applications utilisant l'espace de noms d' <xref:System.Net> est fournie par les classes d' <xref:System.Net.WebPermission> et d' <xref:System.Net.SocketPermission> .  La classe de **WebPermission** contrôle le droit d'une application pour demander des données d'un URI ou pour servir l'URI à Internet.  La classe de **SocketPermission** contrôle le droit d'une application d'utiliser <xref:System.Net.Sockets.Socket> pour recevoir des données sur un port local ou pour contacter des appareils distants à l'aide d'un protocole de transport à une autre adresse, en fonction de l'hôte, le numéro de port, et le protocole de transport de socket.  
  
 La classe d'autorisation à utiliser dépend de votre type d'application.  Les applications qui utilisent <xref:System.Net.WebRequest> et ses descendants doivent utiliser la classe de **WebPermission** pour gérer des autorisations.  Les applications qui utilisent l'accès de socket\- niveau doivent utiliser la classe de **SocketPermission** pour gérer des autorisations.  
  
 **WebPermission** et **SocketPermission** définissent deux autorisations : acceptez et connectez.  Acceptez les l'application accorde la droite de répondre à une connexion entrante d'une autre partie.  Connectez les l'application accorde l'autorisation d'initialiser une connexion à une autre partie.  
  
 Pour les instances de **SocketPermission** , acceptez signifie qu'une application peut recevoir les connexions entrantes sur une adresse de transport locale ; connectez signifie qu'une application peut se connecter à une adresse de transport distante \(ou des local\).  
  
 Pour les instances de **WebPermission** , acceptez signifie qu'une application peut exporter un URI contrôlé par **WebPermission** au monde ; connectez signifie qu'une application peut accéder qu'un URI \(si elle est distante ou locale\).  
  
## Voir aussi  
 [Sécurité](../../../docs/standard/security/index.md)   
 [Sécurité dans la programmation réseau](../../../docs/framework/network-programming/security-in-network-programming.md)