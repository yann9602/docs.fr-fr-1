---
title: "Authentification Internet | Microsoft Docs"
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
  - "authentification (.NET Framework), classes"
  - "IAuthenticationModule, interface"
  - "ICredentialLookup, interface"
  - "classe CredentialCache, à propos de la classe CredentialCache"
  - "recevoir des données, authentification"
  - "classe AuthenticationManager, à propos de la classe AuthenticationManager"
  - "Internet, authentification"
  - "envoyer des données, authentification"
  - "ressources réseau, authentification"
  - "authentification utilisateur, classes d’authentification"
  - "classe NetworkCredential, à propos de la classe NetworkCredential"
  - "authentification client, classes d’authentification"
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Authentification Internet
Les classes d' <xref:System.Net> prennent en charge divers mécanismes d'authentification du client, notamment les méthodes d'authentification standard Internet de base, digest, négocient, NTLM, et authentification Kerberos, ainsi que méthodes personnalisées que vous pouvez créer.  
  
 Les informations d'identification sont stockées dans des classes d' <xref:System.Net.NetworkCredential> et d' <xref:System.Net.CredentialCache> , qui implémentent l'interface d' <xref:System.Net.ICredentials> .  Lorsqu'une de ces classes est interrogé pour les informations d'identification, elle retourne une instance de la classe de **NetworkCredential** .  La procédure d'authentification est géré par la classe d' <xref:System.Net.AuthenticationManager> , et la procédure d'authentification réelle est exécutée par une classe de module d'authentification qui implémente l'interface d' <xref:System.Net.IAuthenticationModule> .  Vous devez enregistrer un module personnalisé d'authentification avec **AuthenticationManager** avant qu'il puisse être utilisé ; les packages pour le de base, digest, négocient, NTLM, et des méthodes d'authentification Kerberos sont stockées par défaut.  
  
 **NetworkCredential** enregistre un ensemble d'informations d'identification associées à une ressource Internet unique identifiée par un URI et les retourne en réponse à un appel à la méthode d' <xref:System.Net.NetworkCredential.GetCredential%2A> .  La classe de **NetworkCredential** est généralement utilisée par les applications qui accèdent à un nombre limité de ressources Internet ou par les applications qui utilisent le même ensemble des informations d'identification dans tous les cas.  
  
 La classe de **CredentialCache** stocke une collection d'informations d'identification pour les différentes ressources web.  Lorsque la méthode d' <xref:System.Net.CredentialCache.GetCredential%2A> est appelée, **CredentialCache** retourne l'ensemble approprié des informations d'identification, tel que déterminé par l'URI de la ressource web et du schéma d'authentification demandé.  Les applications qui utilisent divers ressources Internet avec différents schémas d'authentification qui tirent parti d'utiliser la classe de **CredentialCache** , car elle stocke toutes les informations d'identification et les fournit comme demandées.  
  
 Lorsqu'une ressource Internet demande l'authentification, la méthode d' <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=fullName> envoie <xref:System.Net.WebRequest> à **AuthenticationManager** en même temps que la demande les informations d'identification.  La demande est ensuite authentifiée en fonction de le processus suivant :  
  
1.  **AuthenticationManager** appelle la méthode d' <xref:System.Net.IAuthenticationModule.Authenticate%2A> sur chacun des modules inscrits d'authentification dans l'ordre dans lequel ils ont été enregistrés.  **AuthenticationManager** utilise le premier module qui ne retourne pas **null** pour suivre la procédure d'authentification.  Les détails du processus varie selon le type de module d'authentification impliqué.  
  
2.  Lorsque la procédure d'authentification est terminée, le module d'authentification retourne <xref:System.Net.Authorization> à **WebRequest** qui contient les informations nécessaires pour accéder à la ressource Internet.  
  
 Certains schémas d'authentification peut authentifier un utilisateur sans créer d'abord une demande pour une ressource.  Une application peut gagner du temps par preauthenticating l'utilisateur à la ressource, de ce fait éliminant au moins un aller\-retour vers le serveur.  Ou, elle peut exécuter l'authentification lors de le démarrage du programme pour être plus réactive à l'utilisateur ultérieurement.  Les schémas d'authentification qui peuvent utiliser le preauthentication définissent la propriété de [CanPreAuthenticate](frlrfsystemnetiauthenticationmoduleclasspreauthenticatetopic) à **true**.  
  
## Voir aussi  
 [Authentification de base et authentification Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md)   
 [Authentification NTLM et Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)   
 [Sécurité dans la programmation réseau](../../../docs/framework/network-programming/security-in-network-programming.md)