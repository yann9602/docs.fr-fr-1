---
title: "Regroupement de connexions | Microsoft Docs"
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
  - "internet, connexions"
  - "connexions (.NET Framework), regroupement"
  - "WebRequest (classe), regroupement de connexions"
  - "ressources réseau, connexions"
  - "regroupement de connexions"
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# Regroupement de connexions
Le regroupement de connexion associe les demandes spécifiques dans une même application à un pool de connexions défini.  Cela peut être requis par une application intermédiaire qui se connecte à un serveur principal de la part d'un utilisateur et utilise un fournisseur d'authentification qui prend en charge la délégation, tel que Kerberos, ou par une application intermédiaire qui fournit ses propres informations d'identification, comme dans l'exemple ci\-dessous.  Par exemple, supposons un utilisateur, Joe, visites un site Web interne qui affiche les informations de salaires.  Après avoir authentifié Joe, le serveur d'application intermédiaire utilise les informations d'identification de Joe pour se connecter au serveur principal pour récupérer ses informations de salaires.  Ensuite, Susan visite le site et demande ses informations de salaires.  Étant donné que l'application intermédiaire a déjà établi une connexion à l'aide de les informations d'identification de Joe, le serveur principal répond avec les informations de Joe.  Toutefois, si l'application affecte chaque demande envoyée au serveur principal à un groupe de connexions formé du nom d'utilisateur, puis chaque utilisateur appartient à un pool de connexions distinct et ne peut pas par erreur partager les informations d'identification avec un autre utilisateur.  
  
 Pour assigner une demande à un groupe de connexions spécifique, vous devez assigner un nom à la propriété d' <xref:System.Net.WebRequest.ConnectionGroupName%2A> de votre <xref:System.Net.WebRequest> avant d'effectuer la demande.  
  
## Voir aussi  
 [Gestion des connexions](../../../docs/framework/network-programming/managing-connections.md)   
 [Comment : assigner des informations utilisateur aux connexions de groupe](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)